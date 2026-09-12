# C++ Chess System & Matchmaking Engine ♟️

A robust, console-based Chess System built in C++ that emphasizes **Object-Oriented Programming (OOP)** and **Gang of Four (GoF) Design Patterns**. 

This project simulates a backend architecture for a chess server, featuring piece movement mechanics, check/checkmate detection, player matchmaking based on skill ratings, and an in-game chat system.

## 🚀 Features

* **Full Chess Logic**: Standard piece movements, turn-based mechanics, and capture logic.
* **Game State Detection**: Evaluates Check, Checkmate, and Stalemate conditions.
* **Matchmaking System**: Pairs players from a waiting queue based on score/ELO tolerance.
* **In-Game Chat**: Players can send and receive messages during a live match.
* **Console UI**: Visualizes the board state using an ASCII-based grid with standard algebraic notation.

---

## 🏗️ Design Patterns Implemented

This project acts as a practical showcase of software design patterns. 

### 1. Factory Pattern
* **Location**: `PieceFactory`
* **Use**: Centralizes the creation of chess pieces (`King`, `Queen`, `Rook`, etc.). Instead of directly instantiating pieces, the board requests them from the factory, making the initialization process clean and scalable (e.g., easy to add fairy chess pieces).

### 2. Strategy Pattern
* **Location**: `ChessRules` and `MatchingStrategy`
* **Use**: 
  * encapsulates movement rules (`StandardChessRules`), allowing for future variations like Chess960 or King of the Hill without altering the core `Match` logic.
  * Encapsulates the matchmaking algorithm (`ScoreBasedMatching`), allowing the system to easily swap to a ping-based or random matchmaking system.

### 3. Mediator Pattern
* **Location**: `ChatMediator`, `Match`, and `User` (as `Colleague`)
* **Use**: Handles the chat system between players. Instead of users holding direct references to each other to send messages, they communicate through the `Match` (Mediator), which routes the messages appropriately.

### 4. Singleton Pattern
* **Location**: `GameManager`
* **Use**: Ensures only one instance of the game manager exists at runtime to maintain a single source of truth for the active matches map and the waiting user queue.

---

## 📂 Project Architecture

* **`Position` & `Move`**: Data structures representing board coordinates (0-7) and state transitions.
* **`Piece` (Abstract)**: Base class for all chess pieces defining the `getPossibleMoves()` contract.
* **`Board`**: A "dumb" object that safely manages the 2D grid and memory lifecycle of the pieces.
* **`Match`**: The core controller for a single game. Manages the board, players, current turn, move history, and implements the chat mediator.
* **`GameManager`**: Global orchestrator that matches users and spins up `Match` instances.

---

## 🛠️ Getting Started

### Prerequisites
* A C++ compiler that supports C++11 or higher (e.g., GCC, Clang, or MSVC).

### Compilation & Execution

1. Clone the repository:
   ```bash
   git clone [https://github.com/yourusername/chess-system-cpp.git](https://github.com/yourusername/chess-system-cpp.git)
   cd chess-system-cpp
