# Java Group Chat Application

A pure Java, console‑based group chat application built on TCP sockets. Demonstrates multithreading, socket I/O, and real‑time message broadcasting without external dependencies.

## Description

This repository contains three main components:

- **Server** (`Server.java`):
  - Listens on port `1234`
  - Accepts multiple client connections
  - Spawns a `ClientHandler` thread for each user
  - Broadcasts every incoming message to all connected clients
  - Prints join/disconnect notices to the console

- **ClientHandler** (`ClientHandler.java`):
  - Reads the username sent by the client upon connection
  - Maintains a list of active client handlers
  - Relays each client’s messages to all other users
  - Cleans up and notifies the group when a client disconnects

- **Client** (`Client.java`):
  - Prompts the user for a username
  - Connects to `localhost:1234`
  - Runs a background thread to listen for broadcast messages
  - Reads console input and sends messages to the server
  - Supports `disconnect` to leave chat and `exit` to quit the client application

## Key Features

- **Multi‑Client Support**: Handles multiple users concurrently via dedicated threads.
- **Message Broadcasting**: Seamlessly relays chat messages in real time.
- **Graceful Disconnect**: Users can leave and rejoin without crashing the server.
- **Persistent Logging**: (Optional) Easily extend by logging to a file for record‑keeping.

## Prerequisites

- Java JDK 8 or higher
- (Optional) Maven or Gradle for build management

## Setup & Usage

1. **Clone the repo**
   ```bash
   git clone https://github.com/your-username/java-group-chat.git
   cd java-group-chat
   ```

2. **Compile all sources**
   ```bash
   javac Server.java ClientHandler.java Client.java
   ```

3. **Start the server**
   ```bash
   java Server
   ```
   The server will listen on port `1234` and log connections to the console.

4. **Run one or more clients**
   In separate terminal windows:
   ```bash
   java Client
   ```
   - Type `connect` to join, then enter your username
   - Chat by typing messages and pressing **Enter**
   - Type `disconnect` to leave the chat (you can `connect` again)
   - Type `exit` to terminate the client

## Project Structure

```
├── Server.java         # Main server: listens on port 1234
├── ClientHandler.java  # Manages each client connection in its own thread
├── Client.java         # Console client: user menu, send/receive logic
└── README.md           # Project documentation
```

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
