`use` only creates the shortcut for the particular scope in which the `use` occurs. We can also provide new names for what we bring into scope using the `as` keyword.

```
use std::fmt::Result;
use std::io::Result as IoResult;

fn function1() -> Result {
    // --snip--
}

fn function2() -> IoResult<()> {
    // --snip--
}
```


When we bring a name into scope with the `use` keyword, the name is private to the scope into which we imported it. To enable code outside that scope to refer to that name as if it had been defined in that scope, we can combine `pub` and `use`.

```
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

pub use crate::front_of_house::hosting;

pub fn eat_at_restaurant() {
    hosting::add_to_waitlist();
}
```

like this `hosting` is exported but not with `front_of_house` being public to other modules.


We can also nest paths together :

```
// --snip--
use std::cmp::Ordering;
use std::io;
// --snip--

// --snip--
use std::{cmp::Ordering, io};
// --snip--

------------------------------------

use std::io;
use std::io::Write;

use std::io::{self, Write};
```


or import everything using the `*` operator :

```
use std::collections::*;
```