#### Crate

A **crate** is the smallest unit of compilation in Rust — it's what the compiler operates on at a time. There are two kinds:

- **Binary crate** (`main.rs`) — compiles to an executable
- **Library crate** (`lib.rs`) — compiles to a reusable library (no `main`)

A crate has a **crate root**: the source file the compiler starts from (`src/main.rs` or `src/lib.rs`).

#### Package

A **package** is a bundle of one or more crates, defined by a single `Cargo.toml`. It's what you create when you run `cargo new`.

Rules a package must follow:

- It can contain **at most one library crate**
- It can contain **any number of binary crates** (in `src/bin/`)
- It must contain **at least one crate** (either kind)

#### Concrete example

```
my-project/
├── Cargo.toml          ← defines the package
├── src/
│   ├── main.rs         ← binary crate root (named "my-project")
│   ├── lib.rs          ← library crate root (named "my-project")
│   └── bin/
│       └── tool.rs     ← another binary crate (named "tool") with its own main
						  run with `cargo run --bin tool`
```

This package contains **3 crates**: one library and two binaries.

#### The short version

| Concept     | Defined by         | What it is                                  |
| ----------- | ------------------ | ------------------------------------------- |
| **Crate**   | A root source file | Single compilation unit (binary or library) |
| **Package** | `Cargo.toml`       | A collection of crates with metadata        |

So when you `cargo add serde`, you're adding a **package** as a dependency — but what gets compiled and linked into your project is serde's **library crate**. The terms are often used loosely/interchangeably in conversation, but that's the precise distinction.

