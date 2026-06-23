# Cats & Dogs — Abstract Board Game

A browser-based abstract board game built with vanilla JavaScript, HTML and CSS. The game features a turn-based system, move validation rules, and a simple AI opponent with adjustable difficulty.

## Features

- Turn-based two-player gameplay (Cat vs Dog)
- Single-player mode with AI opponent
- AI difficulty levels: Easy, Normal, Hard, Very Hard
- Rule-based move validation system
- Dynamic highlighting of valid/invalid moves on hover
- End-game detection when a player runs out of valid moves
- Sound effects for moves, alerts, and victory events
- Interactive UI with menus, rules screen, and start screen

## Game Rules

- Players take turns placing pieces on an 8x8 board.
- Cat always starts first and must place its first piece in the center region.
- Dog cannot place its first piece in the center region.
- Pieces cannot be placed adjacent (horizontally or vertically) to an opponent piece.
- The objective is to restrict the opponent’s available moves.
- The game ends when a player has no valid moves left; the last player to make a valid move wins.

## Controls

- Click a square to place a piece
- Hover over squares to preview valid/invalid moves
- Use menus to select:
  - Single player or multiplayer mode
  - AI difficulty
  - Start game / restart game

## AI System

The AI evaluates possible moves by simulating their impact on the opponent’s available moves.

Each potential move is scored based on how many moves it removes from the opponent:
- Best moves: maximize opponent restriction
- Intermediate moves: moderate restriction
- Worst moves: minimal or no restriction

A weighted randomness system is used to adjust difficulty:
- Easy: prefers weaker moves
- Normal: balanced selection
- Hard: favors strong moves
- Very Hard: almost always optimal moves

## Project Structure

```text
/project-root
│
├── index.html # Game UI structure
├── script.js # Game logic, AI, and state management
├── style.css # Visual styling (not included here)
├── Resources/ # Sounds, icons, and assets
```

## Core Logic Overview

### State Management
- `cat` and `dog` objects store player state and valid moves
- `moveNumber` tracks turn order
- `currentPlayer` and `otherPlayer` alternate each move

### Move Validation
- First move rules differ for Cat and Dog
- Subsequent moves must follow adjacency restrictions
- Invalid moves trigger UI error messages and rollback of move counter

### Board Representation
- Board squares are identified using IDs like `A11`, `B22`, etc.
- Internal logic extracts numeric values for validation and AI processing

### AI Logic Flow
1. Generate all possible moves for Dog
2. Simulate each move impact on Cat
3. Categorize moves into best / intermediate / worst
4. Apply weighted randomness based on difficulty
5. Execute selected move

## Audio & Feedback

- Move placement sound
- Error alert sound for invalid moves
- Victory sounds for Cat and Dog
- Background music on start screen

## Limitations / Known Issues

- Heavy reliance on global state variables
- Tight coupling between game logic and DOM manipulation
- Board coordinate system is string-based and fragile
- AI does not use deep search (only immediate move evaluation)

## Possible Improvements

- Refactor into modular architecture (Game / UI / AI separation)
- Replace string-based coordinates with x/y grid system
- Introduce proper state machine for turn handling
- Improve AI with deeper lookahead
- Convert to TypeScript for better maintainability

## License

Personal project — free to use and modify.

---

## Author Notes

This project was built as a learning exercise in:
- JavaScript game logic
- DOM manipulation
- Basic AI decision systems
- UI state management
