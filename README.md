# 🤖 Grandmaster Hybrid Arena Bot

A high-performance, multi-language competitive arena bot designed for 1v1 tactical combat. It features a sophisticated **Hit-and-Run loop**, utilizes all **13 unique combat abilities**, and implements a hybrid architecture combining **Rust**, **Python**, and **C++**.

---

## 🏗️ Architecture & How It Works

To achieve maximum performance and intelligent decision-making, the project splits tasks across three specialized languages:

1. **Rust (`src/main.rs`) - The Master Wrapper:**
   - Compiled as an invisible background process (`#![windows_subsystem = "windows"]`) to prevent GUI interference.
   - Handles high-speed I/O and bridges the communication between the arena and the AI logic via IPC (Inter-Process Communication pipes using `stdin`/`stdout` JSON streams).
2. **Python (`strategy.py`) - The Strategy Engine:**
   - Manages the complex state machine, tactical decision trees, and ability cooldowns.
   - Executes the automated combat loop: *Stun/Strike ➔ Double Dodge Away ➔ Continuous Retreat & Double Shoot ➔ Aggressive Re-engagement*.
3. **C++ (`engine.cpp`) - The Utility Core:**
   - Provides low-level mathematical and physics helper functions for distance evaluation and threat vector calculations.

---

## ✨ Key Features

* **Full Ability Arsenal:** Intelligently switches between all 13 unique moves (including *Shockwave Slam*, *Double Shoot*, *Phase Blink*, *Counter Nova*, *Triple Orbit*, and *Circle Bullet*).
* **Advanced Hit-and-Run Loop:** Automatically strikes close-range targets, performs rapid double-dodges straight away from the opponent (`angle + math.pi`), backs away while raining down projectile fire, and rushes back in when safe.
* **Stealth Execution:** Runs seamlessly in the background as a compiled `.exe` without popping up annoying console windows.
* **Low Latency IPC:** Lightning-fast JSON serialization via `serde_json` ensures zero frame drops in the arena.

---

## 📂 Project Structure

```text
grandmaster_bot/
├── Cargo.toml          # Rust package and dependency configuration
├── engine.cpp          # C++ math and utility core
├── strategy.py         # Python AI and state-machine logic
└── src/
    └── main.rs         # Rust master wrapper & IPC orchestrator
