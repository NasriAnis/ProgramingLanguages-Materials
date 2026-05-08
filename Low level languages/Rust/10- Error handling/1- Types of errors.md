1. Recoverable : such as a _file not found_ error, we most likely just want to report the problem to the user and retry the operation.
2. Unrecoverable : symptoms of bugs, such as trying to access a location beyond the end of an array, and so we want to immediately stop the program.

Rust has the type `Result<T, E>` for recoverable errors and the `panic!` macro that stops execution when the program encounters an unrecoverable error.