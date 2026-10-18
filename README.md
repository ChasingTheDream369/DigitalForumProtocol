# Digital Forum Protocol (DFP)

DFP is a Python-based application-layer protocol for digital forum communication. It implements a multithreaded client-server architecture over TCP sockets, with authentication, command processing, file operations, structured message exchange, and heartbeat-based connection monitoring.

## Overview

The project explores the design and implementation of an application-layer communication protocol, including message formats, client-server coordination, concurrent connection handling, and connection lifecycle management.

## Features

- **Client-server communication:** TCP socket-based communication between clients and the server.
- **Authentication:** Token-based authentication using protocol-defined constants.
- **Command processing:** Structured handling of client commands, server responses, and invalid requests.
- **File operations:** File-related commands, including listing, reading, and supported file management operations.
- **Message serialization:** JSON-encoded payloads for commands that require structured data.
- **Concurrent connections:** Multithreaded server-side client handling with mutex locks for shared-state coordination.
- **Heartbeat monitoring:** A dedicated heartbeat mechanism for monitoring client-server connectivity and handling server shutdown.
- **Protocol state management:** Defined message constants for coordinating interactions and representing protocol states.

## Architecture

The codebase is organised into two components:

### Client

The client establishes a TCP connection with the server, handles authentication, initiates forum interactions, sends commands, and processes server responses.

### Server

The server listens for incoming connections, manages connected clients, processes commands, and coordinates responses. Client connections are handled using separate threads, with synchronisation mechanisms for shared state.

## Protocol Design

DFP uses predefined string constants to represent protocol commands, responses, and state transitions. JSON is used for structured payloads associated with operations such as reading data and listing files.

The implementation also uses a separate socket for heartbeat messages, allowing the client to monitor server availability and respond to server shutdown.

## Implementation

- **Language:** Python
- **Networking:** TCP sockets
- **Concurrency:** Multithreading and mutex locks
- **Data exchange:** JSON and protocol-defined message constants
- **Architecture:** Object-oriented client-server design

## Running the Project

The client and server components are maintained in separate directories. Ensure that the protocol constants module, `DFP_CONSTS.py`, is available in both components.

Start the server using the project's server entry point, then connect a client using the server IP address and port:

```bash
python client.py <Server_IP> <Server_Port>
```

Use the server's configured port and follow the command-line arguments and setup instructions supported by the implementation.

## Design Considerations

The project uses a thread-per-client approach and dedicated heartbeat handling to manage concurrent communication and connection monitoring. Mutex locks coordinate access to shared state.

Potential areas for further development include connection pooling or event-driven I/O, more flexible message encoding, improved connection lifecycle management, and expanded protocol testing.
