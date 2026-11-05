# UDP Socket Programming 

## 1. Basics

**UDP = User Datagram Protocol**

- Connectionless protocol.
    
- No connection establishment.
    
- Delivery and ordering are not guaranteed.
    
- Uses `SOCK_DGRAM`.
    
- Uses `sendto()` and `recvfrom()`.
    

## 2. Import and create socket

```
from socket import *

s = socket(AF_INET, SOCK_DGRAM)
```

- `AF_INET` → IPv4
    
- `SOCK_DGRAM` → UDP
    

Alternative syntax:

```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
```

## 3. Important UDP methods

|Method|Purpose|
|---|---|
|`socket()`|Create socket|
|`bind((host,port))`|Assign local IP and port|
|`sendto(data,address)`|Send datagram|
|`recvfrom(2048)`|Receive bytes and sender address|
|`close()`|Close socket|
|`encode()`|String → Bytes|
|`decode()`|Bytes → String|

## 4. UDP Server — Complete Program

**Receives a message, converts it to uppercase, and sends it back.**

```
from socket import *

serverSocket = socket(AF_INET, SOCK_DGRAM)

serverSocket.bind(('127.0.0.1', 5000))

print("Server ready")

while True:
    message, clientAddress = serverSocket.recvfrom(2048)

    print("Client:", message.decode())

    response = message.decode().upper()

    serverSocket.sendto(
        response.encode(),
        clientAddress
    )
```

### Server sequence

```
socket()
   ↓
bind()
   ↓
recvfrom()
   ↓
Process message
   ↓
sendto()
```

## 5. UDP Client — Complete Program

```
from socket import *

clientSocket = socket(AF_INET, SOCK_DGRAM)

message = input("Enter message: ")

clientSocket.sendto(
    message.encode(),
    ('127.0.0.1', 5000)
)

response, serverAddress = clientSocket.recvfrom(2048)

print("Server:", response.decode())

clientSocket.close()
```

### Client sequence

```
socket()
   ↓
sendto()
   ↓
recvfrom()
   ↓
close()
```

### Expected output

```
Enter message: hello
Server: HELLO
```

## 6. Important syntax explanations

### `bind()`

```
s.bind(('127.0.0.1', 5000))
```

Assigns the local IP and port to the socket.

```
s.bind(('', 5000))
```

Binds to all available local IPv4 interfaces.

### `sendto()`

```
s.sendto(message.encode(), (host, port))
```

- First argument → Data to send (bytes).
    
- Second argument → Destination IP and port.
    

### `recvfrom()`

```
message, address = s.recvfrom(2048)
```

Returns two things:

1. `message` → Received bytes.
    
2. `address` → Sender IP and port.
    

`2048` → Maximum number of bytes to receive.

### `encode()` and `decode()`

```
"hello".encode()    # b'hello'
b'hello'.decode()   # 'hello'
```

## 7. Important PYQ

**2025 Repeat/Repeat-End-Sem — Q4 (12 marks)**

Question: Implement a simple UDP/IP client-server application using Python sockets.

**Answer:** Write the complete UDP server and client programs from Sections 4 and 5.

- Server creates a UDP socket and binds to a port.
    
- Client sends a message using `sendto()`.
    
- Server receives it using `recvfrom()`.
    
- Server processes and sends a response.
    
- Client receives and displays the reply.
    

## 8. Common mistakes

|Wrong|Correct|
|---|---|
|`SOCK_STREAM`|`SOCK_DGRAM`|
|`send()` for the basic unconnected UDP example|`sendto()`|
|`recv()` for the basic UDP example|`recvfrom()`|
|`listen()`|Not required|
|`accept()`|Not required|
|Sending a string directly|Use `.encode()`|

## 9. Last-minute memory

```
# UDP SERVER
s = socket(AF_INET, SOCK_DGRAM)
s.bind((HOST, PORT))
data, addr = s.recvfrom(2048)
s.sendto(response, addr)

# UDP CLIENT
s = socket(AF_INET, SOCK_DGRAM)
s.sendto(message, (HOST, PORT))
data, addr = s.recvfrom(2048)
s.close()
```

Here `message` and `response` must be bytes.

**Remember:**

- UDP → `SOCK_DGRAM`
    
- UDP → `sendto()` + `recvfrom()`
    
- UDP → No `listen()` or `accept()`
    
- UDP → Connectionless