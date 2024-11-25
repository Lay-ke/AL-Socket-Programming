# Documentation for Simple Client-Server Communication using Python Sockets

This documentation describes the implementation of a simple client-server application using Python's `socket` library. It explains how the client and server interact to exchange messages, adhering to network programming best practices.

## Overview

This application consists of:
- **Server**: Waits for incoming client connections, receives a message, and echoes it back to the client.
- **Client**: Connects to the server, sends a message, and prints the response.

---

## Requirements

- **Python version**: 3.x
- **Socket library**: Pre-installed with Python standard library

---

## How It Works

This section explains the flow of communication between the client and server, highlighting their interaction step-by-step.

---

### 1. Server Initialization
- The server creates a socket using `socket.AF_INET` (IPv4) and `socket.SOCK_STREAM` (TCP).
- It binds the socket to an IP address (`127.0.0.1`) and a port (`12345`).
- The server listens for incoming connections with a maximum queue of 5 clients (`listen(5)`).

---

### 2. Client Connection
- The client creates a socket using the same address family (`AF_INET`) and protocol (`SOCK_STREAM`).
- It connects to the server's IP address (`127.0.0.1`) and port (`12345`) using `connect()`.

---

### 3. Message Exchange
- **Client**:
  - Sends a message (`Hello, server!`) to the server using `send()`. The message is encoded as `UTF-8` before transmission.
- **Server**:
  - Accepts the connection using `accept()`, which provides the client socket and address.
  - Receives the message from the client using `recv(1024)` and decodes it to a string.
  - Echoes the message back to the client using `send()`.

---

### 4. Response Handling
- **Client**:
  - Receives the server's response using `recv(1024)` and decodes it to a string.
  - Prints the response (`Received from server: Hello, server!`) to the console.

---

### 5. Clean-Up
- Both the client and server close their respective sockets using `close()`. This releases the resources and ensures proper termination of the connection.

---

### Summary of Communication
1. **Server** starts and listens for connections.
2. **Client** connects to the server.
3. **Client** sends a message to the server.
4. **Server** receives the message and sends it back (echoes).
5. **Client** prints the echoed message.
6. Both sockets are closed, ending the communication.

## How to Run

Follow these steps to run the client-server application:

---

### 1. Start the Server
1. Open a terminal or command prompt.
2. Run the server script using the following command:
   ```bash
   python server.py

- You should see `Server listening on 127.0.0.1:12345` indicating server is ready to accept request

### 2. Start the Client
1. Open another terminal or command prompt
2. Run the client script using the following command:
    ```bash
   python client.py

- Once it is runned it sends a request to the server which returns `Received from server: Hello, server!`.
