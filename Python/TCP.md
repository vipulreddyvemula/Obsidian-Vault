# TCP Socket Programming — Syntax Revision

## 1. Basics

**TCP = Transmission Control Protocol**

- Connection-oriented.
    
- Reliable and ordered byte-stream delivery.
    
- Establishes connection before sending application data.
    
- Uses `SOCK_STREAM`.
    
- Typically uses `connect()`, `sendall()`, `recv()`, `listen()` and `accept()`.
    

## 2. Import and create TCP socket

```
from socket import *

s = socket(AF_INET, SOCK_STREAM)
```

- `AF_INET` → IPv4
    
- `SOCK_STREAM` → TCP
    

## 3. Important TCP methods

|Method|Purpose|
|---|---|
|`socket()`|Create socket|
|`bind()`|Assign local IP and port|
|`listen(5)`|Listen for incoming connections|
|`accept()`|Accept a client connection|
|`connect()`|Connect to server|
|`send()`|Send some or all supplied bytes|
|`sendall()`|Send all supplied bytes or raise an error|
|`recv(1024)`|Receive up to 1024 bytes|
|`close()`|Close socket|

## 4. TCP Server — Complete Program

**November 2025 End Sem — Q4 (10 marks)**

Server receives a message, prints it, and replies `"Message received"`.

```
from socket import *

serverSocket = socket(AF_INET, SOCK_STREAM)

serverSocket.bind(('127.0.0.1', 12000))

serverSocket.listen(5)

print("Server waiting...")

connectionSocket, addr = serverSocket.accept()

message = connectionSocket.recv(1024).decode()

print("Client:", message)

connectionSocket.sendall(
    "Message received".encode()
)

connectionSocket.close()
serverSocket.close()
```

### TCP server sequence

```
socket()
   ↓
bind()
   ↓
listen()
   ↓
accept()
   ↓
recv()
   ↓
sendall()
   ↓
close()
```

## 5. TCP Client — Complete Program

**November 2025 End Sem — Q4 (10 marks)**

```
from socket import *

clientSocket = socket(AF_INET, SOCK_STREAM)

clientSocket.connect(('127.0.0.1', 12000))

clientSocket.sendall(
    "Hello Server".encode()
)

reply = clientSocket.recv(1024).decode()

print("Server:", reply)

clientSocket.close()
```

### TCP client sequence

```
socket()
   ↓
connect()
   ↓
sendall()
   ↓
recv()
   ↓
close()
```

### Expected output

Server:

```
Server waiting...
Client: Hello Server
```

Client:

```
Server: Message received
```

## 6. Important syntax explanations

### `bind()`

```
serverSocket.bind(('127.0.0.1', 12000))
```

Associates server socket with IP and port.

### `listen()`

```
serverSocket.listen(5)
```

Enables listening for connections.

`5` → Requested backlog of pending connections, NOT maximum total clients.

### `accept()`

```
connectionSocket, addr = serverSocket.accept()
```

Returns:

1. `connectionSocket` → New connected socket for client communication.
    
2. `addr` → Client IP and port.
    

### `connect()`

```
clientSocket.connect(('127.0.0.1', 12000))
```

Establishes TCP connection.

### `sendall()`

```
clientSocket.sendall(message.encode())
```

Sends all supplied bytes unless an error occurs.

### `recv()`

```
data = connectionSocket.recv(1024)
```

Receives **up to** 1024 bytes.

It may return fewer bytes, so large data should be received in a loop.

### Why two sockets on TCP server?

```
serverSocket       # Listening socket

connectionSocket   # Communication with accepted client
```

`accept()` creates/returns the new connected socket.

## 7. TCP uppercase program — Faculty example

To convert a client's message to uppercase, change the server processing logic:

```
message = connectionSocket.recv(1024).decode()

response = message.upper()

connectionSocket.sendall(response.encode())
```

Example:

```
Client sends: hello
Server replies: HELLO
```

All remaining TCP code stays the same.

## 8. Actual PYQ — PDF File Transfer (10 marks)

**PYQ guide — Q9, alternative (OR) question**

Computer A sends a PDF to Computer B.

**Choose TCP (connection-oriented)** because reliable, ordered transfer is needed.

### Server — Computer B (Receiver)

```
from socket import *

s = socket(AF_INET, SOCK_STREAM)

s.bind(('', 5001))
s.listen(1)

conn, addr = s.accept()

with open("received.pdf", "wb") as f:
    while True:
        data = conn.recv(4096)

        if not data:
            break

        f.write(data)

print("File received")

conn.close()
s.close()
```

### Client — Computer A (Sender)

```
from socket import *

s = socket(AF_INET, SOCK_STREAM)

s.connect(('127.0.0.1', 5001))

with open("document.pdf", "rb") as f:
    while True:
        data = f.read(4096)

        if not data:
            break

        s.sendall(data)

print("File sent")

s.close()
```

Use the receiver's actual reachable IP instead of `127.0.0.1` when transferring between different computers.

### Important file-transfer syntax

```
open("document.pdf", "rb")  # Read binary

open("received.pdf", "wb")  # Write binary

f.read(4096)               # Read up to 4096 bytes

conn.recv(4096)            # Receive up to 4096 bytes

s.sendall(data)            # Send full chunk

f.write(data)              # Write received bytes
```

`if not data: break` → No more data to read or receive.

Do NOT use `.encode()` or `.decode()` for PDF contents. They are already bytes.

## 9. Common TCP mistakes

|Wrong|Correct|
|---|---|
|`SOCK_DGRAM`|`SOCK_STREAM`|
|Forgetting `listen()`|Server must listen|
|Forgetting `accept()`|Server accepts client|
|Calling `accept()` on client|Client uses `connect()`|
|Using `recvfrom()` in basic TCP example|Use `recv()`|
|Sending a string directly|Use `.encode()`|
|Assuming one `recv()` reads entire file|Receive in a loop|
|Using `"r"` for PDF|Use `"rb"`|
|Using `"w"` for PDF|Use `"wb"`|

## 10. Last-minute memory

```
# TCP SERVER
s = socket(AF_INET, SOCK_STREAM)
s.bind((HOST, PORT))
s.listen(5)
conn, addr = s.accept()
data = conn.recv(1024)
conn.sendall(response)
conn.close()
s.close()

# TCP CLIENT
s = socket(AF_INET, SOCK_STREAM)
s.connect((HOST, PORT))
s.sendall(message)
data = s.recv(1024)
s.close()
```

`message` and `response` are bytes.

**Remember:**

- TCP → `SOCK_STREAM`
    
- TCP server → `bind()`, `listen()`, `accept()`
    
- TCP client → `connect()`
    
- TCP communication → `sendall()`, `recv()`
    
- TCP file transfer → `rb`, `wb`, loop, `sendall()`