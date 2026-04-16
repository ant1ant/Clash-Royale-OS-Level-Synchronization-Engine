## Clash Royale OS-Level Synchronization Engine
A high-performance, automated game server engine written in C that simulates the core backend logic of Clash Royale. This project focuses on solving critical Operating Systems challenges, including Deadlock Prevention, Thread Synchronization, and Inter-Process Communication (IPC).

### Project Overview
The server simulates a real-time multiplayer environment where automated Card Spawners (Threads) concurrently deploy characters (Troops) into a shared Arena (Bounded Buffer) using a global Elixir pool (Shared Resource).

### Key OS Concepts Implemented
- Concurrency: Multi-threaded architecture using pthread to simulate independent card spawner routines.
- Deadlock Prevention: Implemented "Hold-and-Wait" prevention by ensuring atomic acquisition of Elixir resources.
- Synchronization: Utilized Semaphores and Mutexes to solve the classic Producer-Consumer problem within the Arena buffer.
- IPC (Inter-Process Communication): Implementation of a unidirectional Pipe for a dedicated Battle Logger thread to handle live text feeds.
- Signal Handling: Custom interrupt handlers for SIGINT (Ctrl+C) to ensure graceful server shutdown and final statistics reporting.

### Technical Specifications
The server's logic is mathematically tied to specific constraints (derived from university SRN):

Arena Capacity: 5+(SRN(mod5)) slots.

Max Elixir Capacity: 10+(SRN(mod3)) drops.

### How to Run
Compile the code
```bash
gcc clash_server.c -o clash_server -lpthread
```
Execute the server
```bash
./clash_server
```
Terminate: Press Ctrl+C to trigger the match_over_handler, which will display final game stats and exit gracefully.
