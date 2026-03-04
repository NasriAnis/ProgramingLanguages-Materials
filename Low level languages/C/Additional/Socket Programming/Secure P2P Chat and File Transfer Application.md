## Introduction

This document provides a deep dive into the design and implementation of a secure, peer-to-peer (P2P) chat and file-sharing application written in C. The goal of this document is to not only explain how the application works but also to provide a solid foundation for understanding the underlying concepts of socket programming, cryptography, and P2P application development.
## Core Concepts

### Peer-to-Peer (P2P) Networking

In a traditional client-server model, all clients connect to a central server. The server is responsible for relaying messages between clients. In a P2P model, however, clients (or "peers") connect directly to each other without the need for a central server.

**Advantages of P2P:**

*   **No Single Point of Failure:** If a central server goes down, the entire network is offline. In a P2P network, the network remains operational as long as there are peers connected.

*   **Censorship Resistance:** It is much harder to shut down a P2P network as there is no central server to target.

*   **Scalability:** In a client-server model, the server can become a bottleneck as the number of clients increases. In a P2P network, the capacity of the network grows as more peers join.

  

**Challenges of P2P:**

  

*   **Peer Discovery:** How do peers find each other in the first place? In a client-server model, the server's address is well-known. In a P2P network, we need a mechanism for peers to discover each other's IP addresses.

*   **NAT Traversal:** Most devices on the internet are behind a Network Address Translation (NAT) device (like a router). This means they don't have a public IP address, which makes it difficult for peers to connect to them directly. We will explore techniques to overcome this, such as hole punching.

  

### Socket Programming

  

Socket programming is the foundation of network communication. A socket is an endpoint for sending or receiving data across a computer network. We will be using the Berkeley sockets API, which is the standard for socket programming in C.

  

We will be using TCP (Transmission Control Protocol) for our application. TCP is a connection-oriented protocol that provides reliable, ordered, and error-checked delivery of a stream of bytes.

  

### Cryptography

  

To secure our communication, we will use the `libsodium` library. `libsodium` is a modern and easy-to-use cryptographic library. We will use it for:

  

*   **Key Exchange:** To securely establish a shared secret key between two peers.

*   **Authenticated Encryption:** To encrypt our messages in a way that also provides integrity and authenticity. This means we can be sure that our messages are not being read or tampered with by a third party.

  

## Application Architecture

  

Our application will be divided into several modules:

  

*   **`main.c`:** The entry point of our application. It will handle command-line arguments and initialize the other modules.

*   **`network.c` / `network.h`:** This module will be responsible for all the low-level networking code, such as creating sockets, listening for connections, and sending and receiving data.

*   **`crypto.c` / `crypto.h`:** This module will handle all the cryptographic operations, such as key exchange and encryption/decryption.

*   **`chat.c` / `chat.h`:** This module will implement the chat functionality, including the user interface.

*   **`file_transfer.c` / `file_transfer.h`:** This module will implement the file transfer functionality.

  

This modular design will make the code easier to understand, maintain, and extend.

  

## Phase 1: Foundational P2P Chat (Insecure)

  

In this first phase, we have focused on the basic P2P networking logic. We have created a simple chat application where two peers can connect to each other and exchange messages. This version is not secure, but it provides a solid foundation for the next phases.

  

### Code Explanation

  

#### `Makefile`

  

The `Makefile` is a simple script that automates the compilation process. It defines the compiler (`gcc`), the compiler flags (`-Wall -g`), the libraries to link against (`-lsodium`), and the source files. The `all` target builds the entire project, and the `clean` target removes the compiled files.

  

#### `network.h`

  

This header file defines the interface for our networking module. It declares the functions that are implemented in `network.c`. This is good practice as it allows us to separate the interface from the implementation.

  

#### `network.c`

  

This file contains the core networking logic. Let's go through the functions:

  

*   `create_socket()`: This function creates a new TCP socket using the `socket()` system call. `AF_INET` specifies the IPv4 protocol, and `SOCK_STREAM` specifies a TCP socket.

*   `bind_socket()`: This function binds the socket to a specific port on the local machine. This is necessary for the listening peer so that the connecting peer knows where to connect.

*   `start_listening()`: This function puts the socket in a listening state, waiting for incoming connections.

*   `accept_connection()`: This function accepts an incoming connection and returns a new socket file descriptor for the connection. The original listening socket is still open and can accept more connections (though in our current design, it only accepts one).

*   `connect_to_peer()`: This function is used by the connecting peer to establish a connection with the listening peer.

  

#### `chat.h`

  

This header file defines the interface for the chat module.

  

#### `chat.c`

  

This file implements the user interface for the chat. The `start_chat()` function is the heart of this module. It uses the `select()` system call to monitor both the standard input (for user input) and the socket (for incoming messages). This allows the user to type messages and receive messages at the same time, without blocking.

  

#### `main.c`

  

This is the entry point of our application. It parses the command-line arguments to determine whether to act as a listening peer or a connecting peer.

  

*   If the user provides only a port number, the application will act as a listening peer. It will create a socket, bind it to the specified port, and wait for a connection.

*   If the user provides an IP address and a port number, the application will act as a connecting peer. It will create a socket and connect to the specified peer.

  

Once a connection is established, the `start_chat()` function is called to begin the chat session.

  

### How to Compile and Run (Phase 1)

  

To compile the application, you will need `gcc` and `make` installed. You will also need to install the `libsodium` library. On a Debian-based system, you can install it with:

  

```bash

sudo apt-get install libsodium-dev

```

  

Then, you can compile the application by running `make` in the `secure_chat_p2p` directory.

  

To run the application, you will need two terminals.

  

**In the first terminal (the listening peer):**

  

```bash

./p2p_chat 8080

```

  

This will start the application and make it listen for connections on port 8080.

  

**In the second terminal (the connecting peer):**

  

```bash

./p2p_chat 127.0.0.1 8080

```

  

This will connect to the listening peer at `127.0.0.1` (localhost) on port 8080. You can now type messages in both terminals and they will be sent to the other peer.

  

## Phase 2: Secure Communication

  

In this phase, we have integrated the `libsodium` library to secure the communication channel. We are using a key exchange algorithm to establish a shared secret, and then using that secret to encrypt and decrypt messages.

  

### Code Explanation

  

#### `crypto.h`

  

This header file defines the interface for our cryptography module. It defines the `secure_session_t` struct, which holds the session keys for a secure connection. It also declares the functions for key generation, key exchange, encryption, and decryption.

  

#### `crypto.c`

  

This file implements the cryptographic functions using `libsodium`.

  

*   `crypto_init()`: This function initializes the `libsodium` library. It must be called before any other `libsodium` function.

*   `crypto_generate_keypair()`: This function generates a public and secret key pair for the key exchange, using `crypto_kx_keypair()`.

*   `crypto_perform_key_exchange_server()` and `crypto_perform_key_exchange_client()`: These functions perform the key exchange. The process is as follows:

    1.  The client sends its public key to the server.

    2.  The server receives the client's public key and sends its own public key to the client.

    3.  Both the client and the server can now compute the shared session keys using their own secret key and the other party's public key. `libsodium` provides two session keys: one for receiving (`rx`) and one for sending (`tx`). This is important because it prevents replay attacks.

*   `crypto_encrypt()`: This function encrypts a message using `crypto_secretbox_easy()`. This is an authenticated encryption scheme, which means it provides both confidentiality and integrity. It takes a plaintext message, a key, and a nonce (a number that should only be used once per key) and produces a ciphertext. We prepend the nonce to the ciphertext so that the decrypting party can use it.

*   `crypto_decrypt()`: This function decrypts a message using `crypto_secretbox_open_easy()`. It takes a ciphertext, a key, and a nonce and produces the original plaintext. If the ciphertext has been tampered with, this function will fail.

  

#### `main.c` (Changes)

  

The `main.c` file has been updated to:

1.  Initialize `libsodium` by calling `crypto_init()`.

2.  Generate a key pair for the peer.

3.  Call the appropriate key exchange function (`crypto_perform_key_exchange_server()` or `crypto_perform_key_exchange_client()`) after the TCP connection is established.

4.  Pass the `secure_session_t` object to the `start_chat()` function.

  

#### `chat.c` (Changes)

  

The `chat.c` file has been updated to:

1.  Encrypt outgoing messages using `crypto_encrypt()` before sending them over the socket.

2.  Decrypt incoming messages using `crypto_decrypt()` before printing them to the screen.

  

### How to Compile and Run (Phase 2)

  

The compilation and execution process is the same as in Phase 1. Now, all communication between the peers is encrypted.

  

## Phase 3: File Transfer

  

In this phase, we have added the ability to send and receive files. This is done by reading the file in chunks, encrypting each chunk, and sending it over the socket.

  

### Code Explanation

  

#### `file_transfer.h`

  

This header file defines the interface for the file transfer module.

  

#### `file_transfer.c`

  

This file implements the file transfer logic.

  

*   `send_file()`: This function reads the specified file in chunks, encrypts each chunk using `crypto_encrypt()`, and sends it over the socket. To ensure the receiver knows the size of each chunk, we first send the size of the encrypted chunk, and then the chunk itself. When the file transfer is complete, we send a zero-length message to signal the end of the transfer.

*   `receive_file()`: This function receives the file from the peer. It first reads the size of the incoming chunk, then the chunk itself. It then decrypts the chunk using `crypto_decrypt()` and writes the decrypted data to the specified file. When it receives a zero-length message, it knows that the file transfer is complete.

  

#### `chat.c` (Changes)

  

The `chat.c` file has been updated to include two new commands:

  

*   `/send <filename>`: This command will send the specified file to the peer.

*   `/receive <filename>`: This command will receive a file from the peer and save it with the specified filename.

  

### How to Use File Transfer

  

1.  The receiving peer must first type `/receive <filename>` to tell the application to start listening for an incoming file.

2.  The sending peer can then type `/send <filename>` to send the file.

  

This concludes the implementation of the secure chat and file transfer application. The final phase, user identification, is a complex topic with many possible solutions. The current implementation uses IP addresses for identification, which is simple but not very user-friendly. A more advanced solution would involve a centralized discovery server or a decentralized mechanism like a DHT. However, this is beyond the scope of this tutorial.