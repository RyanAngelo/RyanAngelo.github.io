---
layout: page
title: Rust Go
permalink: /projects/rust-go/
collection: projects
---

<span class="icon icon--github">{% include icon-github.svg %}</span> [View on GitHub](https://github.com/RyanAngelo/rust-go){:target="_blank"}

Rust Go is a modern implementation of the ancient board game Go (also known as Weiqi or Baduk) built using Rust and the Bevy game engine. This project combines the strategic depth of one of the world's oldest board games with modern game development practices and Rust's performance guarantees.

The project was born from a desire to explore game development in Rust while implementing the complex rule system that makes Go such a fascinating and challenging game. It serves as both a playable game and a demonstration of Rust's capabilities in interactive application development.

## About the Game of Go

Go is a strategic board game for two players that originated in China over 4,000 years ago. Players alternately place black and white stones on a grid, with the goal of controlling more territory than their opponent. Despite having simple rules, Go is considered one of the most complex games ever created, with more possible board positions than there are atoms in the observable universe.

## Technical Implementation

### Game Engine: Bevy
The project leverages the **Bevy game engine**, a modern, data-driven game engine built in Rust. Bevy's Entity Component System (ECS) architecture provides:
- **Performance**: Efficient parallel processing of game systems
- **Modularity**: Clean separation of game logic and rendering
- **Flexibility**: Easy extension and modification of game features

### Core Architecture

#### Game Logic (`src/game.rs`)
- **Rule Implementation**: Complete Go rule system including capture mechanics
- **Territory Calculation**: Algorithms for determining controlled territory
- **Game State Management**: Turn tracking, move validation, and game end detection
- **Stone Capture Logic**: Implementation of the capture rules that define Go strategy

#### Board Visualization (`src/grid.rs`)
- **Interactive Grid**: Visual representation of the 19x19 Go board
- **Stone Rendering**: Dynamic placement and rendering of black and white stones
- **User Interaction**: Mouse input handling for stone placement
- **Visual Feedback**: Hover effects and move validation indicators

#### Application Entry Point (`src/main.rs`)
- **Bevy Setup**: Game engine initialization and configuration
- **System Registration**: Integration of game logic with rendering systems
- **Resource Management**: Efficient handling of game assets and state

## Development Features

### Performance Optimization
The project includes several performance optimizations:
- **Dynamic Linking**: Optional Bevy dynamic linking for faster compilation during development
- **Optimized Profiles**: Custom Cargo profiles with level 1 optimization for development builds
- **Dependency Optimization**: Level 3 optimization for dependencies to maintain runtime performance

### Development Workflow
```rust
// Fast development builds with dynamic linking
cargo run --features "bevy/dynamic_linking"

// Full test suite
cargo test

// Production build
cargo build --release
```

### Cross-Platform Support
Built with cross-platform compatibility in mind, supporting:
- **Linux**: Full development environment with required system dependencies
- **Windows**: Native Windows support through Rust's toolchain
- **macOS**: Native macOS support with optimized performance

## Technical Challenges

### Rule Complexity
Implementing Go's deceptively simple rules required careful consideration of:
- **Ko Rule**: Preventing infinite loops in stone capture
- **Suicide Rule**: Handling moves that would capture one's own stones
- **Territory Scoring**: Complex algorithms for end-game territory calculation
- **Group Management**: Efficient tracking of connected stone groups

### Performance Considerations
- **Large State Space**: Managing the complexity of 19x19 board positions
- **Real-time Interaction**: Maintaining smooth user interaction while processing complex game logic
- **Memory Management**: Efficient handling of game state and history

### Bevy Integration
- **ECS Architecture**: Adapting traditional game logic to Entity Component System patterns
- **Rendering Pipeline**: Integrating custom game rendering with Bevy's rendering systems
- **Input Handling**: Mapping mouse interactions to board coordinates and game actions


[Back](/)
