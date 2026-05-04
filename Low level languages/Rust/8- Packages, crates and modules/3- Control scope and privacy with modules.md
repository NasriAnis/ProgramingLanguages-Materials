Paths : allow to name items (functions, structs, and enums)
`use` : bring items into scope through the path
`pub` : make items public

### Modules

modules allow us to organize related code into the same block :

```
mod front_of_house {
    mod hosting {
        fn add_to_waitlist() {}

        fn seat_at_table() {}
    }

    mod serving {
        fn take_order() {}

        fn serve_order() {}

        fn take_payment() {}
    }
}
```

```
crate
 └── front_of_house
     ├── hosting
     │   ├── add_to_waitlist
     │   └── seat_at_table
     └── serving
         ├── take_order
         ├── serve_order
         └── take_payment
```

### Cheat Sheet

Crate root : `main.rs` or `lib.rs`
Path to code inside a module : we use the `::` to navigate
pub vs private : using the `pub` before `mod` makes it public
bringing `mod` into scope : `use` keyword followed by the path

Declaring modules : `mod`, then the compiler search for  
- Inline, within curly brackets that replace the semicolon following `mod <name>`
- In the file `src/<mod-created>.rs`
- In the file `src/<mod-created>/mod.rs`

Declaring sub modules : using `mod` inside `mod` blocks
- Inline, directly following `mod <name>`, within curly brackets instead of the semicolon
- In the file `src/<parent-module>/<mod-name>.rs`
- In the file `src/<parent-module>/<mod-name>/mod.rs`


