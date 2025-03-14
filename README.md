# Blackjack Network Multiplayer

A simple networked Blackjack game written in C. The project consists of a server and a client application that communicate over TCP/IP sockets. Server discovery is handled via IPv4/IPv6 multicast. Rankings are saved to a file, and the server can run as a background daemon.

## Features
- Multiplayer Blackjack server supporting up to 10 players.
- Server IP discovery using multicast (IPv4 and IPv6).
- Daemonized server process with syslog logging.
- Player rankings with persistent storage.
- Interactive text-based client supporting both IP versions.

## How it works
- **Server**:
  - Runs as a daemon, listening for incoming connections.
  - Broadcasts its IP address over multicast.
  - Manages game sessions, player statistics, and rankings.
  
- **Client**:
  - Discovers the server via multicast.
  - Connects and interacts with the server to play Blackjack.
  - Supports both IPv4 and IPv6.

## Getting Started

### Prerequisites
- A Linux/Unix environment.
- GCC or another C compiler.
- Root privileges (recommended for binding to multicast and managing daemon processes).

### Compilation
```bash
gcc serwer_blackjack.c -o blackjack_server -lpthread
gcc klient_blackjack.c -o blackjack_client
