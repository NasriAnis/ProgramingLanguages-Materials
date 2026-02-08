## Types of socket
- `sock_stream` which use TCP protocol
- `sock_dgram` which use UDP protocol
# Byte order
To send and receive data from one computer to another it has to be transformed in decimals to hexadecimal integer like `2f0a` that is a two bytes integer `2f` and `0a`. This integer can be stored in two different way 2f followed by 0a "big endian" or in some particular intel processor it prefer storing it backward "little endian" 0a then 2f. The incompatibility can cause issues during data transfer. The network byte order is always in big endian.
## Converting to and from network byte order
The host system is not storing its bytes in the same order compared to the network thus we need to reorder them when transferring between the network and the host system. For this we need the `<arpa/inet.h>` library.
```c
uint32_t htonl(uint32_t hostlong);  //"Host to network long"
uint16_t htons(uint16_t hostshort); //"Host to network short"
uint32_t ntohl(uint32_t netlong);   //"Network to host long"
uint16_t ntohs(uint16_t netshort);  //"Network to host short"
```
s we can see, these functions come in two variants: the ones that convert a `short` (two bytes, or 16 bits), and those that convert a `long` (four bytes or 32 bits). They also work for unsigned integers.

In order to convert a four byte (32 bit) integer from the Host Byte Order to the Network Byte Order, we’ll want to call the `htonl()` function (“htonl” stands for “Host to Network Long”). For the opposite operation, we’d use `ntohl()` (“Network to Host Long”).
# Preparing a connection
First of all we need to prepare a small data structure that will contain information that our socket will need.

- Using the `<netinet/in.h>` library we can specify the structure for the connection IP address and port like IPv4 or IPv6.
#### For IPv4 address
`sockaddr_in` is used as follow :
```c
// IPv4 only (see sockaddr_in6 for IPv6)
struct sockaddr_in {
    sa_family_t    sin_family;
    in_port_t      sin_port;
    struct in_addr sin_addr; //nested struct inside the sockdde_in
};

struct in_addr {
    uint32_t       s_addr;
};

struct sockaddr_in server_addr; server_addr.sin_family = AF_INET;  server_addr.sin_port = htons(8080);  server_addr.sin_addr.s_addr = inet_addr("127.0.0.1"); 
```
- `sin_family` : represent the family of the protocol since the structure can only be used for IPv4 we will always indicate the AF_INET
- `sin_port` : the port where we connect Warning: we must supply this port number in the _Network Byte Order_, not the host order. For example, to connect to port 3302, we will need to use `htons()` to indicate it here: `htons(3302)`.
- `sin_addr` : a small structure of type `in_addr`, which contains the integer representation of an IPv4 address.
##### Some explanation before we continue
**The nested structure concept:**

When you see this:
````c
struct sockaddr_in {
    sa_family_t    sin_family;
    in_port_t      sin_port;
    struct in_addr sin_addr;     // <-- This line
};
```

The line `struct in_addr sin_addr;` means: "Inside `sockaddr_in`, there is a variable called `sin_addr`, and its type is `struct in_addr`."

**Think of it like boxes inside boxes:**
```
sockaddr_in (the big box)
├── sin_family  (a simple value)
├── sin_port    (a simple value)  
└── sin_addr    (a small box inside the big box)
    └── s_addr  (the actual IP address number)
````

**Why have a box inside a box?**

Instead of just putting the IP address directly like this:
```c
struct sockaddr_in {
    sa_family_t sin_family;
    in_port_t   sin_port;
    uint32_t    ip_address;  // Direct - simpler but less organized
};
```

They wrapped it in its own structure:
```c
struct sockaddr_in {
    sa_family_t    sin_family;
    in_port_t      sin_port;
    struct in_addr sin_addr;  // Wrapped - more organized
};
```

**Real-world analogy:**
Think of it like an address:
- `sockaddr_in` = complete mailing address
- `sin_family` = country code
- `sin_port` = apartment number
- `sin_addr` = street address (which itself contains the street number inside)

**In code:**
```c
struct sockaddr_in server;

// Setting simple fields:
server.sin_family = AF_INET;     // Direct access
server.sin_port = htons(8080);   // Direct access

// Setting the nested field:
server.sin_addr.s_addr = htonl(INADDR_ANY);
//     └─ first go into the sin_addr box
//              └─ then access s_addr inside that box
```

##### .
In the `in_addr` structure there is only one field `s_addr` to fill it is the network byte order integer that represent an IPv4 address (below is explained how to convert an ip to an integer),  without forgetting to convert the order of their bytes with `htonl()`:

- `INADDR_LOOPBACK`: the local machine’s IP address: localhost, or `127.0.0.1`
- **`INADDR_ANY`**: the IP address `0.0.0.0`
- **`INADDR_BROADCAST`**: the IP address `255.255.255.255`
#### For IPv6
A similar structure exists to specify an IPv6 address:

```c
// IPv6 only (see sockaddr_in for IPv4)
struct sockaddr_in6 {
    sa_family_t     sin6_family;
    in_port_t       sin6_port;
    uint32_t        sin6_flowinfo;
    struct in6_addr sin6_addr;
    uint32_t        sin6_scope_id;
};
struct in6_addr {
    unsigned char   s6_addr[16];
};
```
`sockaddr_in6`, expects the same information as the previous IPv4 structure
#### Converting IP address to an integer
From the `<arpa/inet.h>` library we call `inet_pton()` (“pton” stands for “presentation to network”) to convert a string of character to an integer.
```c
int inet_pton(int af, const char * src, void *dst);
```
- **af**: an integer that represents the address’ family of Internet protocols. For an IPv4 address, we will want `AF_INET` here; for an IPv6 address, `AF_INET6`.
- **src**: a string containing the IPv4 or IPv6 address to convert.
- **dst**: a pointer to an `in_addr` (IPv4) or `in6_addr` (IPv6) structure in which to store the result of the conversion.

The `inet_pton()` function returns:
- 1 to indicate success,
- 0 if _src_ does not contain a valid address for the indicated address family,
- -1 if _af_ is not a valid address family, in which case it sets errno to `EAFNOSUPPORT`.

To convert an IPv4 address, we can do something like this:

```c
// IPv4 only
struct sockaddr_in sa;
inet_pton(AF_INET, "216.58.192.3", &(sa.sin_addr));
```

For an IPv6 address:

```c
// IPv6 only
struct sockaddr_in6 sa;
inet_pton(AF_INET6, "2001:db8:0:85a3::ac1f:8001", &(sa.sin6_addr));
```

the opposite function exists as well, `inet_ntop()` (“ntop” meaning “network to presentation”). It allows us to convert an integer into a legible IP address.
## Automatically fill in the IP address with getaddrinfo()
If the exact IP is not known then we use the `etaddrinfo()` function from the `<netdb.h>` it allows us to supply a domain name ( `http://www.example.com`) instead of an IP address.
```c
int getaddrinfo(const char *node, const char *service,
                const struct addrinfo *hints,
                struct addrinfo **res);
```
- **node**: a string representing an IP address (IPv4 or IPv6), or a domain name like “[www.example.com](https://www.example.com)”. Here, we can also indicate `NULL` if we supply the right flags to the _hints_ structure described below (for example, if we want to automatically fill the localhost address).
- **service**: a string representing the port we’d like to connect to, such as “80”, or the name of the service to connect to, like “http”. On a Unix system, the list of available services and their ports can be found in `/etc/services`. This list is also available online on [iana.org](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml).
- **hints**: a pointer to an `addrinfo` structure where we can supply more information about the connection we want to establish. The hints we provide here act as a kind of search filter for `getaddrinfo()`. We will examine this structure more closely below.
- **res**: a pointer to a linked list of `addrinfo` structures where `getaddrinfo()` can store its result(s).

The `getaddrinfo()` function returns 0 on success, or an error code on failure. The `gai_strerror()` can translate the error returned by `getaddrinfo()` into a readable string.

#### The addrinfo structure
the `freeaddrinfo()` function allows us to free the memory of the `addrinfo` once we’re done with it.
```c
struct addrinfo {
    int              ai_flags;
    int              ai_family;
    int              ai_socktype;
    int              ai_protocol;
    size_t           ai_addrlen;
    struct sockaddr *ai_addr;
    char            *ai_canonname;
    struct addrinfo *ai_next;
};
```

The `addrinfo` structure contains the following elements:

- **ai_flags**: flags containing options that we can combine with a [bitwise OR](https://www.codequoi.com/en/binary-010-uses-of-bit-shifting-and-bitwise-operations/). Here, the most interesting flag that we might want to use is `AI_PASSIVE`, which indicates that the socket we will create will be used to listen for and accept connections in the context of a socket. In this case, we won’t need to indicate an IP address when we call `getaddrinfo()`, since the IP will be that of the machine. A list of all of the available flags can be found on the [[)](https://man7.org/linux/man-pages/man3/getaddrinfo.3.html|manual page for getaddrinfo()]].
- **ai_family**: the address family of Internet protocols. To force an IPv4 address, we can indicate `AF_INET`; to force an IPv6 address, `AF_INET6`. One advantage here is that we can make our code IP-agnostic by indicating `AF_UNSPEC`. In this case, `getaddrinfo()` will return IPv4 and IPv6 addresses.
- **ai_socktype**: the type of socket we’d like to create with the address. Two constants are available here: `SOCK_STREAM`, which uses TCP, and `SOCK_DGRAM`, which uses UDP. We can also indicate 0 here, to tell `getaddrinfo()` that it can return any type of socket address.
- **ai_protocol**: the protocol of the socket address. In general, there is only one valid protocol for each socket type - TCP for a stream socket, UDP for a datagram socket -, so we can safely put 0 here to tell `getaddrinfo()` that is can return any type of addresses.
- **ai_addrlen**: `getaddrinfo()` will indicate the length of the address here.
- **ai_addr**: a pointer to a `sockaddr_in` or `sockaddr_in6`, which we’ve seen previously, which `getaddrinfo()` will fill out for us.
- **ai_canonname**: only used if the `AI_CANONNAME` flag is set in _ai_flags_.
- **ai_next**: a pointer to the next element in the linked list.
#### Getaddrinfo() Example
```c
// showip.c -- a simple programme the shows a domain name's IP address(es)
#include <arpa/inet.h>
#include <netdb.h>
#include <stdio.h>
#include <string.h>

int main(int ac, char **av) {
    struct addrinfo hints; // Hints or "filters" for getaddrinfo()
    struct addrinfo *res;  // Result of getaddrinfo()
    struct addrinfo *r;    // Pointer to iterate on results
    int status; // Return value of getaddrinfo()
    char buffer[INET6_ADDRSTRLEN]; // Buffer to convert IP address

    if (ac != 2) {
        fprintf(stderr, "usage: /a.out hostname\n");
        return (1);
    }

    memset(&hints, 0, sizeof hints); // Initialize the structure
    hints.ai_family = AF_UNSPEC; // IPv4 or IPv6
    hints.ai_socktype = SOCK_STREAM; // TCP

    // Get the associated IP address(es)
    status = getaddrinfo(av[1], 0, &hints, &res);
    if (status != 0) { // error !
        fprintf(stderr, "getaddrinfo: %s\n", gai_strerror(status));
        return (2);
    }

    printf("IP adresses for %s:\n", av[1]);

    r = res;
    while (r != NULL) {
        void *addr; // Pointer to IP address
        if (r->ai_family == AF_INET) { // IPv4
            // we need to cast the address as a sockaddr_in structure to
            // get the IP address, since ai_addr might be either
            // sockaddr_in (IPv4) or sockaddr_in6 (IPv6)
            struct sockaddr_in *ipv4 = (struct sockaddr_in *)r->ai_addr;
            // Convert the integer into a legible IP address string
            inet_ntop(r->ai_family, &(ipv4->sin_addr), buffer, sizeof buffer);
            printf("IPv4: %s\n", buffer);
        } else { // IPv6
            struct sockaddr_in6 *ipv6 = (struct sockaddr_in6 *)r->ai_addr;
            inet_ntop(r->ai_family, &(ipv6->sin6_addr), buffer, sizeof buffer);
            printf("IPv6: %s\n", buffer);
        }
        r = r->ai_next; // Next address in getaddrinfo()'s results
    }
    freeaddrinfo(res); // Free memory
    return (0);
}
```
# Preparing sockets
From the library `<sys/socket.h>` we call `socket()` to create a file descriptor for our socket to read and write received and sent data.

```c
int socket(int domain, int type, int protocol);
```
- **domain**: the socket’s protocol family, generally `PF_INET` or `PF_INET6`. `PF_INET` exists for historical reasons and is, in practice, identical to `AF_INET`. The same is true for `PF_INET6`.
- **type**: the type of socket, generally `SOCK_STREAM` or `SOCK_DGRAM`.
- **protocol**: the protocol to use with the socket. In general, there is only one valid protocol by socket type, TCP for a stream socket and UDP for a datagram socket, which means we can safely put 0 here.

The `socket()` function returns the file descriptor of the new socket. In case of failure, it returns -1 and indicates the error it encountered in `errno`.

## Chat gpt explanation
### 🧠 **The context**

This code is about **network programming in C**, specifically about **connecting to another computer (a server) through the Internet** — like how your browser connects to `www.example.com`.

To do that, the program needs:

1. To **find out the server’s address** (IP, port, protocol, etc.).
    
2. To **create a socket** — a sort of “doorway” your program uses to talk to that server.
    

---

### 🔹 `int status;`

This variable will store **the result (success or failure)** of certain functions.  
If a function works fine, it usually returns `0`.  
If it fails, it returns a **non-zero number**, and you can then look up what that means.

🧩 Example:

```c
status = getaddrinfo(...);
if (status != 0) {
    printf("Something went wrong!\n");
}
```

---

### 🔹 `int socket_fd;`

This is the **file descriptor** of your socket.  
In C, a socket is treated like a file — you can **read** and **write** to it just like a file.

Once you create a socket successfully, this variable will hold a small number (like 3 or 4) that identifies it.

🧩 Example:

```c
socket_fd = socket(...);
if (socket_fd == -1) {
    printf("Socket creation failed!\n");
}
```

---

### 🔹 `struct addrinfo hints;`

This `hints` structure tells the system **what kind of network connection you want** — for example:

- IPv4 or IPv6?
    
- TCP or UDP?
    

You “fill out” this structure before calling `getaddrinfo()` to give it hints about your needs.

🧩 Example:

```c
memset(&hints, 0, sizeof hints);
hints.ai_family = AF_INET;       // IPv4
hints.ai_socktype = SOCK_STREAM; // TCP
```

---

### 🔹 `struct addrinfo *res;`

This is a **pointer** that will store the **result** from `getaddrinfo()`.  
After calling `getaddrinfo()`, `res` will point to a list of possible server addresses your program can connect to.

🧩 Example:  
After you do:

```c
getaddrinfo("www.example.com", "http", &hints, &res);
```

the variable `res` might now point to an address like:

```
93.184.216.34  (the IP of www.example.com)
Port: 80 (because “http” means port 80)
```

---

### 🔹 `status = getaddrinfo("www.example.com", "http", &hints, &res);`

This line **translates the human-readable server name** (`"www.example.com"`) and service (`"http"`) into a computer-usable address (IP + port).

If it fails, `status` will be non-zero.

🧩 Example:

- Input: `"www.example.com"`, `"http"`
    
- Output in `res`: IP address like `"93.184.216.34"`, port `80`
    

It’s like asking a directory service:

> “Hey, where can I find [www.example.com](http://www.example.com) for HTTP?”

---

### 🔹 `socket_fd = socket(res->ai_family, res->ai_socktype, res->ai_protocol);`

This line **creates the socket** using the information from `res`.  
It tells the OS:

> “Give me a communication channel that can talk to this kind of server (IPv4/IPv6, TCP/UDP, etc.).”

If successful, you can now use `socket_fd` to connect, send, and receive data.

🧩 Example:

- `res->ai_family` → `AF_INET` (IPv4)
    
- `res->ai_socktype` → `SOCK_STREAM` (TCP)
    
- `res->ai_protocol` → `IPPROTO_TCP`
    

So this might create a **TCP socket** for IPv4 communication.

---

### 🧩 **Putting it all together**

Here’s a simplified “story” of what’s happening:

1. You describe what kind of connection you want (with `hints`).
    
2. You ask the system, “Where is [www.example.com](http://www.example.com) for HTTP?” (`getaddrinfo`)
    
3. The system gives you an address (`res`).
    
4. You open a door (socket) to talk to that address (`socket()`).
    

After this, you can call `connect(socket_fd, res->ai_addr, res->ai_addrlen)` to actually connect and then `send()` / `recv()` to talk with the server.


```c
int status;
int socket_fd;
struct addrinfo hints;
struct addrinfo *res;

// fill out hints to prepare getaddrinfo() call

status = getaddrinfo("www.example.com", "http", &hints, &res);
// check if getaddrinfo() failed

socket_fd = socket(res->ai_family, res->ai_socktype, res->ai_protocol);
// check if socket() failed
```

In practice, we probably won’t be filling out the `socket()` function’s parameters manually.

But this socket file descriptor is not yet connected to anything at all. Naturally, we will want to associate it to a socket address (meaning an IP address and port combination). For this, we have two choices:

- Connect the socket to a remote address with `connect()`. This will allow it to work as a client, able to make requests to a remote server.
- Connect the socket to a local address with `bind()`. In this case, it will work as a server, able to accept connections from remote clients.
# Client side: Connecting to a server via a socket
We use the `connect()` system call from the **`<sys/socket.h>`** library
```c
int connect(int sockfd, const struct sockaddr *serv_addr,
            socklen_t addrlen);
```
- **sockfd**: the socket file descriptor we got from our call to `socket()`,
- **serv_addr**: a pointer to the structure containing the connection information. This will either be `sockaddr_in` for an IPv4 address, or `sockaddr_in6` for an IPv6 address.
- **addrlen**: the size in bytes of the previous structure, `serv_addr`.

The function predictably returns 0 in for success and -1 for failure, with `errno` set to indicate the error.

Once more, all of the data needed for the connection can be found in the structure returned by `getaddrinfo()`:

```c
int status;
int socket_fd;
struct addrinfo hints;
struct addrinfo *res;

// fill out hints to prepare getaddrinfo() call

status = getaddrinfo("www.example.com", "http", &hints, &res);
// check if getaddrinfo() failed

socket_fd = socket(res->ai_family, res->ai_socktype, res->ai_protocol);
// check if socket() failed

connect(socket_fd, res->ai_addr, res->ai_addrlen);
```

There we go! Our socket is now ready to send and receive data. But before we get to how to do that, let’s first take a look at establishing a connection from the server side.
# Server Side: Accepting Client Connections via a Socket
steps to be done for a connection if we we want to develop  server:
1. bind our socket to a local address and port
2. listen to the port to detect incoming connection requests
3. accept those client connection requests
## Binding the socket to the local address
The `bind()` function of `<sys/socket.h>` allows us to link our socket to a local address and port. Practically identical to its twin function `connect()`, which we examined for the client side:
```c
int bind(int sockfd, const struct sockaddr *addr, socklen_t addrlen);
```
Just like `connect()`, the parameters of `bind()` are:

- **sockfd**: the socket file descriptor we got with our call to `socket()`.
- **addr**: a pointer to the structure containing the connection information. This is either a `sockaddr_in` for an IPv4 address, or a `sockaddr_in6` for an IPv6 address.
- **addrlen**: the size in bytes of the previous structure, `addr`.

As expected, the function returns 0 for success and -1 to indicate an error, with the error code in `errno`.
## Listening via a socket to detect connection requests
For this, we will use the `listen()` function, which is also in **`<sys/socket.h>`**.

```c
int listen(int sockfd, int backlog);
```

The `listen()` function takes two parameters:

- **sockfd**: the socket file descriptor that we got with the call to `socket()`.
- **backlong**: an integer representing the number of connection requests allowed in the queue. Incoming connections will be placed in this queue until we accept them. Most systems automatically cap the number of pending connection requests to 20, but we can manually specify this maximum as we wish.

If the call to `listen()` succeeds, the function returns 0. If it fails, it returns -1 and sets `errno` accordingly.
## Accepting a client connection
Finally, we must accept the connection requests from a remote client. When a client `connect()` s on the port of our machine that our socket is `listen()` ing to, its request is put in the pending queue. When we `accept()` the request, that function will return a new file descriptor bound to the client’s address, through which we will be able to communicate with that client. So we will end up with two file descriptors: our initial socket that will continue listening to our port, and a new file descriptor for the client, which we can use to send and receive data.

The prototype of the `accept()` function of `<sys/socket.h>` is as follows:

```c
int accept(int sockfd, struct sockaddr *addr, socklen_t *addrlen);
```

Let’s take a closer look at its parameters:

- **sockfd**: the listening socket’s file descriptor, which we got with the call to `socket()`.
- **addr**: a pointer to a `sockaddr` structure where `accept()` can fill out the information related to the client socket. If we don’t want to save the client’s address or port number, we can just put `NULL` here.
- **addrlen**: a pointer to an integer which contains the size in bytes of the previous structure. `accept()` will adjust this value if it is too large for the final size of the structure, but it will truncate the address if this value is smaller than the final size of the address.

The `accept()` function returns the file descriptor of the new socket, or -1 in case it encounters an error, which it indicates in `errno`.