```
TERMINAL 1 (Server)              TERMINAL 2 (Client)
─────────────────────            ─────────────────────

./server
✓ Socket created
✓ Bound to port 8080
✓ Listening...
Waiting for connections...
                                 ./client
                                 ✓ Socket created
                                 Connecting to server...
                                 
      <── TCP Handshake ──>      
      (happens automatically)
      
✓ Client connected!              ✓ Connected to server!

                                 You: Hello Server!
Received: Hello Server!          [message travels through network]
Echoed back to client            
                                 Server echoed: Hello Server!
                                 
                                 You: How are you?
Received: How are you?           [message travels through network]
Echoed back to client
                                 Server echoed: How are you?

[continues...]
```

---

## **What's Actually Happening**

### **1. Before Connection**
```
Server                           Client
  │                                │
  │ socket() ──> [Socket created]  │
  │ bind()   ──> [Bound to port]   │
  │ listen() ──> [Ready for conn]  │
  │ accept() ──> [WAITING...]       │
```

### **2. Client Connects**
```
Server                           Client
  │                                │
  │ accept() [WAITING...]          │ socket() ──> [Socket created]
  │                                │ connect() ──> [Tries to connect]
  │                                │
  │ <────── SYN packet ───────────│  (TCP handshake)
  │ ─────── SYN-ACK ─────────────>│
  │ <────── ACK ──────────────────│
  │                                │
  │ accept() returns!              │ connect() returns!
  │ [Connection established]       │ [Connection established]
```

### **3. Data Exchange**
```
Server                           Client
  │                                │
  │                                │ send("Hello") ──> [Data flows]
  │ recv() ──> Gets "Hello"        │                    through
  │                                │                    network
  │ send("Hello") ──> [Echo back]  │
  │                                │ recv() ──> Gets "Hello"
  │                                │
```

---

## **The Beautiful Part**

Once connected, **it's a two-way pipe**:
```
     ┌─────────────────────────────────┐
     │    Established TCP Connection    │
     │                                  │
Server│◄────────────────────────────────│Client
     │                                  │
     │────────────────────────────────►│
     │      Data flows both ways!       │
     └─────────────────────────────────┘
```

- **Server can send to client**: `send(client_fd, data, ...)`
- **Client can send to server**: `send(sock_fd, data, ...)`
- **Both can receive**: `recv(...)`
- Messages go through the **actual network** (even on localhost, it goes through network stack)

---

## **Real Network Path (even on localhost)**

When you type "Hello" on the client:
```
1. Client program: send() call
   ↓
2. Operating system: TCP layer
   ↓
3. Network stack: Adds TCP/IP headers
   ↓
4. Loopback interface (127.0.0.1)
   ↓
5. Operating system: Receives packet
   ↓
6. TCP layer: Strips headers
   ↓
7. Server program: recv() returns data
```