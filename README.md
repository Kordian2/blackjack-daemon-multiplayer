# Blackjack Network Multiplayer

The project implements the card game Blackjack, where the server manages the gameplay and clients act as players. The server supports simultaneous connections of multiple clients and allows individual gameplay. The server runs in the background as a daemon. The server's address is broadcast over the network using multicast. Client names are associated by the server, which then allows viewing of rankings (wins, draws, losses).


## Features
- Multiplayer Blackjack server supporting up to 10 players.
- Server IP discovery using multicast (IPv4 and IPv6).
- Daemonized server process with syslog logging.
- Player rankings with persistent storage.
- Interactive text-based client supporting both IP versions.

## How it works

- The server sends its IPv4 or IPv6 address to the MULTICAST address (239.255.255.250 for IPv4 or ff02::1 for IPv6) every 5 seconds, depending on your choice.
- Depending on your choice, the client configures itself to listen on the appropriate multicast address (IPv4 or IPv6) and waits for the server IP.

### Choose IP version:
1. IPv4
3. IPv6

- After receiving the server's IP address, the client establishes a TCP connection to the server and displays the information
- The server asks the client for a name
- The server then asks the client to choose one of three options:
  Welcome <name>! Choose an option: 1. Play Blackjack 2. View Rankings 3. Exit
- Depending on the choice made by the player, the server proceeds to the game, shows the rankings, or terminates the client.

## Getting Started

### Prerequisites
- A Linux/Unix environment.
- GCC or another C compiler.
- Root privileges (recommended for binding to multicast and managing daemon processes).

### Compilation
```bash
gcc serwer_blackjack.c -o blackjack_server -lpthread
gcc klient_blackjack.c -o blackjack_client
