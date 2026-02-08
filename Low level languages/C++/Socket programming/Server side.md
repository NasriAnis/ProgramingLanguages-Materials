to use these option we need to import the <sys/socket.h> header file.

note:
```
struct sockaddr_in  // IPv4
struct sockaddr_in6 // IPv6
struct sockaddr_un  // Unix domain sockets
```
# socket()
the socket() is a system call in network programming that creates a new socket.

syntax:
`int sockfd = socket(AF_INET, SOCK_STREAM, 0);`

- the sockfd declares an integer variable that will store the file descriptor
- AF_INET indicates the socket that it will use IPv4
- SOCK_STREAM specifies that the socket will use TCP
- **0** lets the system choose the default protocol for the specified address family and socket type (which is TCP in this case).
# bind()
this method is associated with a socket with a specific local address and port number which allows the socket to listen to incoming connection on that address.

syntax:
`bind(sockfd, (struct sockaddr*)&address, sizeof(address));`

- sockfd represent the file descriptor for the socket
- (struct sockaddr_)&address casts the address structure to a generic pointer type for the bind function.
- sizeof(address) specifies the size of the address structure to inform the system how much data to expect.
# listen()
