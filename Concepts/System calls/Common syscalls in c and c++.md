
| Category            | System Call (Function) | Description                                                   | Header File                          |
| ------------------- | ---------------------- | ------------------------------------------------------------- | ------------------------------------ |
| **File I/O**        | `open()`               | Opens a file and returns a file descriptor.                   | `<fcntl.h>`                          |
|                     | `read()`               | Reads data from a file descriptor into a buffer.              | `<unistd.h>`                         |
|                     | `write()`              | Writes data from a buffer to a file descriptor.               | `<unistd.h>`                         |
|                     | `close()`              | Closes an opened file descriptor.                             | `<unistd.h>`                         |
| **Process Control** | `fork()`               | Creates a new child process by duplicating the parent.        | `<unistd.h>`                         |
|                     | `exec()` family        | Replaces the current process image with a new program.        | `<unistd.h>`                         |
|                     | `wait()`               | Suspends the parent process until a child process terminates. | `<sys/wait.h>`                       |
|                     | `exit()`               | Terminates the current process.                               | `<stdlib.h>` (for C std lib version) |
| **Utility**         | `system()`             | Executes an external command using the OS shell.              | `<stdlib.h>` / `<cstdlib>`           |
