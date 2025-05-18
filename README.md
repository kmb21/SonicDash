# Sonic Dash for NES (Homebrew Game)

## Overview

**Sonic Dash** is a fast-paced, side-scrolling homebrew NES game inspired by endless runners. Developed in C using the [cc65](https://cc65.github.io/cc65/) toolchain and NESLib, it features smooth animations, a colorful tilemap-based environment, musical score playback, and gameplay mechanics including coins, powerups, and obstacles.

This project showcases how classic game development constraints (limited memory, tile-based graphics, simple audio hardware) can still produce engaging and replayable gameplay using clever optimizations and system-level programming.

---

## Gameplay Instructions

* **Objective**: Dodge obstacles, collect coins and powerups to achieve a high score.
* **Controls** (using NES pad or emulator equivalent):

  * **Left/Right**: Move Sonic between 3 fixed lanes.
  * **Up/Down**: Slight vertical adjustment (useful for dodging or collecting).
  * **Start**: Begin or restart the game.
* **Coins**: +1 point. Randomly spawn in lanes.
* **Walls**: Colliding ends the game. Avoid at all costs!
* **Powerups**: +5 points and temporarily slow down coin speed, making collection easier.

---

## Key Features

* **NES Graphics**: Custom palettes, tilemap rendering with `vram_put`, multi-directional scrolling.
* **Audio System**: APU programming with pitch tables, pulse/triangle channels, and musical byte stream.
* **Sprite Animation**: Double-buffered frames with leg animation and collision-based changes.
* **Collision Detection**: Axis-aligned bounding box checks for walls, coins, and powerups.
* **Performance-Efficient Drawing**: Sprites composed of 4 tiles for Sonic, wall extensions drawn dynamically.
* **Game State Handling**: Title screen, game over screen, and soft reset with assembly jump.

---

## Technologies Used

* **NESLib & CC65**: Libraries and compiler toolchain for 6502 ASM/C hybrid development.
* **APU Programming**: Direct manipulation of NES's audio hardware for music and effects.
* **VRAM Manipulation**: Direct control of PPU registers for tile and sprite rendering.
* **Fixed Resource Management**: Score displayed via `itoa` conversion to 8x8 sprites.

---

## Motivation

The project was born out of a desire to:

* Explore **low-level programming** through retro hardware.
* Build a fully playable game on the **limited NES platform** (2KB RAM, 256 tiles).
* Recreate the spirit of Sonic with NES-era authenticity.
* Learn and demonstrate **frame-perfect timing**, APU audio, and PPU tile control.

This kind of development fosters deep appreciation for modern tools, and teaches:

* Memory optimization
* Graphics compression
* Real-time input handling
* Fixed-point math and timing-based game loops

---

## How It Can Inspire Game Development

* **Constraint-based design** encourages elegant solutions and optimization.
* **Low-level debugging** builds stronger intuition for performance tradeoffs.
* **Working with real-time systems** trains your mind in multitasking, timing, and animation syncing.
* **Audio sequencing and APU work** introduces concepts that are useful for embedded game sound design.
* **Designing a full game loop** from scratch helps reinforce fundamentals of state machines, input polling, and rendering cycles.

---

## How to Play the Game

1. Use an NES emulator (e.g., **FCEUX**, **Mesen**) and load the compiled ROM.
2. Use keyboard or controller to:

   * Press **Start** to begin.
   * Move Sonic **left/right** to switch lanes.
   * Use **up/down** to adjust position.
3. Collect **coins** and **powerups**, avoid **walls**.
4. When you lose, press **Start** to reset.

---

## Build and Run

### Prerequisites:

* `cc65` (with `cl65`, `ca65`, `ld65`)
* NES emulator (e.g., [FCEUX](http://fceux.com/), [Mesen](https://www.mesen.ca/))

### Compilation:

```bash
cl65 -t nes -o sonic_dash.nes main.c apu.c bcd.c vrambuf.c
```

### Execution:

Load `sonic_dash.nes` in your emulator of choice.

---

## Credits

* **Developer**: Maxwell Kumbong
* **Tools**: cc65, NESLib, FCEUX
* **Music System**: Custom APU pulse/triangle pattern-based playback
* **Special Thanks**: Retro game dev community and resources like Nerdy Nights and NESDev Wiki


> *"Working with constraints isn’t limiting – it’s liberating. The NES teaches you how to think like a real game engine."*
