# It's On Heat: An FPGA-Based Interactive Sports Gaming Device

A Harry Potter-themed interactive gaming device combining FPGA technology with physical interaction, developed as the final project for the 2024 Hardware Design and Lab course at National Tsing Hua University.

## Overview

"It's On Heat" is an innovative sports gaming device that combines FPGA technology with interactive hardware, creating an immersive gaming experience inspired by the magical world of Harry Potter. Players must navigate through fire hazards to capture the Golden Snitch, using physical game tiles as the primary input mechanism.

![Game Hardware Design Overview](assets/hardware_overview.jpg)

## Features

### Hardware Components
- FPGA core processing unit
- Custom-designed game tiles with conductive materials
- Arduino Nano 33 IoT for sound playback
- VGA display output
- Physical interaction through stepping tiles

## Software Architecture

### Block Diagram
![System Block Diagram](assets/whole_block_diagram.png)
![System Block Diagram](assets/block_diagram_1.png)
![System Block Diagram](assets/block_diagram_2.png)

The software system consists of several key modules:

#### Game Controller Module
- Central processing unit managing game logic
- Implements FSM for game state control
- Handles fire pattern generation and gold management
- Manages collision detection system

#### Display Controller Module
- Manages VGA rendering (640x480 resolution)
- Handles memory management for sprites and images
- Controls animation system with frame counting
- Implements layering system for proper element visibility

### Finite State Machine (FSM)
![Game State Machine](assets/fsm.png)

The game operates in three main states:
- **INIT**: Initial state, displays title screen
- **PLAY**: Main gameplay state, processes:
  - Player movement
  - Collision detection
  - Score/life management
  - Pattern generation
- **FINISH**: End state (WIN/LOSS conditions)
  - Transitions to WIN when score reaches 3
  - Transitions to LOSS when life reaches 0

### Game Mechanics
- Three game states: INIT, PLAY, and FINISH
- 5 lives system with health deduction on fire contact
- Score tracking through Golden Snitch collection
- Dynamic fire pattern generation every 2 seconds
- Preview system for upcoming fire patterns
- Real-time collision detection

### Visual and Audio Elements
- Six-frame animations for fire hazards and Golden Snitch
- Multiple game screens (title, playing field, win/loss)
- Dynamic background music and sound effects
- Life counter and score display
- Next-pattern preview grid

## System Architecture

![Hardware Connection Overview](assets/hardware_connection.jpg)

### Physical Design
- 3x3 grid of interactive tiles
- Durable construction with improved signal stability
- Jump wire implementation for reliable signal transmission
- Enhanced switch mechanism with foam adhesive and elastic bands

## Implementation Details

### Game Logic Implementation
1. **Fire Pattern Generation**
   - LFSR-based pattern generation
   - 2-second update cycle (clk_div28)
   - Pattern complexity control with masking
   - Dynamic pattern validation

2. **Collision Detection System**
   - Edge-triggered detection mechanism
   - 9-bit hit bitmap implementation
   - Separate handling for fire damage and gold collection
   - State-based visibility control

3. **Animation System**
   - 6-frame sprite animation system
   - 20-bit counter for frame timing
   - Separate memory blocks for different sprite types
   - Transparency handling for smooth rendering

4. **Memory Management**
   - Block RAM utilization for sprite storage
   - Efficient address calculation
   - Multiple image resource handling
   - Dynamic memory access control

## Technical Challenges & Solutions

1. **Signal Stability**
   - Replaced aluminum foil with jump wires
   - Implemented additional circuit resistance
   - Added reinforcement for physical durability

2. **Collision Detection**
   - Introduced check_collision flag system
   - Implemented 9-bit hit_bitmap tracking
   - Enhanced score increment control

3. **User Interface**
   - Developed mini-grid preview system
   - Optimized visual feedback mechanisms
   - Integrated transparent sprite rendering

## Team Members

- **Yu Chia-Suan (余佳軒)**
  - Role: Verilog Game Logic Design
  - Department: Computer Science, NTHU

- **Chang Shun-Han (張舜涵)**
  - Role: Hardware and Circuit Design
  - Department: Computer Science, NTHU

## Documentation

- [Detailed Project Report](docs/final_project_report.pdf)
- [Project Presentation](docs/presentation.pdf)
- [Demo Video](https://youtube.com/your_video_link)

## Setup and Installation

[To be added: Installation instructions, dependencies, and setup guide]

## Development

This project is developed using:
- Verilog for FPGA programming
- Custom circuit design for physical interfaces
- Arduino programming for audio control

## Future Improvements

- Expansion to different game genres
- Enhanced hardware durability
- Additional gameplay features
- Potential parkour-style game integration

## License

[To be added: License information]

---

*Developed as part of the 2024 Hardware Design and Lab course at National Tsing Hua University*
