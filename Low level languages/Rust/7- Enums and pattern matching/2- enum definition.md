enums are defined using the `enum` key word :

```
enum IpAddrKind {
	V4,
	V6,
}

struct IpAddr {
	kind: IpAddrKind,
	address: String,
}

let home = IpAddr {
	kind: IpAddrKind::V4,
	address: String::from("127.0.0.1"),
};

let loopback = IpAddr {
	kind: IpAddrKind::V6,
	address: String::from("::1"),
};
```

enums can also take values and methods :

```
fn main() {
    enum Message {
        Quit,
        Move { x: i32, y: i32 },
        Write(String),
        ChangeColor(i32, i32, i32),
    }

    impl Message {
        fn call(&self) {
            // method body would be defined here
        }
    }

    let m = Message::Write(String::from("hello"));
    m.call();
}
```

there it took a value of a struct type :

```
struct Ipv4Addr {
    // --snip--
}

struct Ipv6Addr {
    // --snip--
}

enum IpAddr {
    V4(Ipv4Addr),
    V6(Ipv6Addr),
}
```