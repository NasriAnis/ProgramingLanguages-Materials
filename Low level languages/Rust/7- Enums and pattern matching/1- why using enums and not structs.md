### The Core Difference

| Struct         | Enum                                     |                                       |
| -------------- | ---------------------------------------- | ------------------------------------- |
| **Represents** | A thing with multiple fields **at once** | One of several **possible variants**  |
| **Data**       | All fields always exist                  | Only the active variant's data exists |
| **Use case**   | Grouping related data together           | Expressing mutually exclusive states  |

Think of it this way:

- **Struct** → "A user _has_ a name, an age, and an email"
- **Enum** → "A packet is _either_ a SYN, ACK, or DATA — never all three at once"

---
### Basic Enum vs Struct

```rust
// Struct: ALL fields exist simultaneously
struct Point {
    x: f64,
    y: f64,
}

// Enum: only ONE variant is active at a time
enum Direction {
    North,
    South,
    East,
    West,
}
```

---

### The Killer Feature: Enums Can Carry Data Per Variant

This is what makes Rust enums radically more powerful than enums in C or most other languages. Each variant can hold **different types and amounts of data**:

```rust
enum Message {
    Quit,                          // no data
    Move { x: i32, y: i32 },      // named fields (like a struct)
    Write(String),                 // single value
    ChangeColor(u8, u8, u8),       // tuple of values
}
```

You **cannot** do this with a struct — a struct always has all its fields. An enum says "it's exactly one of these shapes."

---

### Pattern Matching with `match`

Enums are designed to be used with `match` — this is where they truly shine:

```rust
fn handle_message(msg: Message) {
    match msg {
        Message::Quit => println!("Quitting"),
        Message::Move { x, y } => println!("Moving to ({}, {})", x, y),
        Message::Write(text) => println!("Writing: {}", text),
        Message::ChangeColor(r, g, b) => println!("Color: #{:02X}{:02X}{:02X}", r, g, b),
    }
}
```

The compiler **forces** you to handle every variant. Miss one → compile error. This is exhaustiveness checking and it prevents entire classes of bugs.

---

### Real-World Scenarios

#### 1. Network Packet Parsing (relevant to your raw sockets project)

```rust
enum Packet {
    Icmp { type_: u8, code: u8, payload: Vec<u8> },
    Tcp  { src_port: u16, dst_port: u16, flags: u8, payload: Vec<u8> },
    Udp  { src_port: u16, dst_port: u16, payload: Vec<u8> },
    Unknown(Vec<u8>),
}

fn process(pkt: Packet) {
    match pkt {
        Packet::Icmp { type_, code, .. } => {
            println!("ICMP type={} code={}", type_, code);
        }
        Packet::Tcp { src_port, dst_port, flags, .. } => {
            println!("TCP {}→{} flags=0x{:02X}", src_port, dst_port, flags);
        }
        Packet::Udp { src_port, dst_port, .. } => {
            println!("UDP {}→{}", src_port, dst_port);
        }
        Packet::Unknown(raw) => {
            println!("Unknown proto, {} bytes", raw.len());
        }
    }
}
```

A struct can't model this — a TCP packet and an ICMP packet have completely different layouts.

---

#### 2. `Option<T>` — Rust's null replacement

`Option` is just a built-in enum:

```rust
enum Option<T> {
    Some(T),
    None,
}
```

```rust
fn find_port(service: &str) -> Option<u16> {
    match service {
        "http"  => Some(80),
        "https" => Some(443),
        "ssh"   => Some(22),
        _       => None,
    }
}

// Compiler FORCES you to handle the None case
match find_port("ftp") {
    Some(port) => println!("Port: {}", port),
    None       => println!("Unknown service"),
}
```

No null pointer dereferences. Ever. The type system prevents it.

---

#### 3. `Result<T, E>` — Error handling

Also just an enum:

```rust
enum Result<T, E> {
    Ok(T),
    Err(E),
}
```

```rust
#[derive(Debug)]
enum ParseError {
    InvalidMagic,
    TruncatedHeader,
    UnsupportedVersion(u8),
}

fn parse_header(buf: &[u8]) -> Result<Header, ParseError> {
    if buf.len() < 4 {
        return Err(ParseError::TruncatedHeader);
    }
    if &buf[0..2] != b"\x7fEL" {
        return Err(ParseError::InvalidMagic);
    }
    if buf[2] > 2 {
        return Err(ParseError::UnsupportedVersion(buf[2]));
    }
    Ok(Header { /* ... */ })
}

match parse_header(&data) {
    Ok(hdr)                            => println!("Parsed: {:?}", hdr),
    Err(ParseError::InvalidMagic)      => eprintln!("Not an ELF file"),
    Err(ParseError::TruncatedHeader)   => eprintln!("Buffer too small"),
    Err(ParseError::UnsupportedVersion(v)) => eprintln!("Version {} not supported", v),
}
```

---

#### 4. State Machines (great for exploit dev / protocol impl)

```rust
enum ConnectionState {
    Closed,
    SynSent { seq: u32 },
    Established { seq: u32, ack: u32 },
    FinWait { last_seq: u32 },
}

fn next_state(state: ConnectionState, event: &str) -> ConnectionState {
    match (state, event) {
        (ConnectionState::Closed, "connect")       => ConnectionState::SynSent { seq: 1000 },
        (ConnectionState::SynSent { seq }, "synack") => ConnectionState::Established { seq, ack: seq + 1 },
        (ConnectionState::Established { seq, .. }, "close") => ConnectionState::FinWait { last_seq: seq },
        (s, _) => s, // stay in current state on unknown events
    }
}
```

This is impossible to represent cleanly with structs — the data that _exists_ depends on the _state_.

---

### Quick Summary

```
When you know what fields exist → Struct
When you need to express "one of these possibilities" → Enum

Struct = Product type  (A AND B AND C)
Enum   = Sum type      (A OR  B OR  C)
```

The combination of **data-carrying variants** + **exhaustive `match`** is what makes Rust enums a proper algebraic data type — much closer to Haskell/OCaml than to C enums. Once it clicks, you'll find yourself reaching for enums constantly.