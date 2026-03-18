# 🖥️ Minecraft CPU Project: Overview

Welcome to the flagship engineering project of **CodeHive**. We are designing and constructing a functional, programmable 8-bit Computer-on-a-Chip entirely within Minecraft using Redstone logic.

## 🎯 Project Objective
The goal of this project is to bridge the gap between high-level programming and low-level digital electronics. By the end of this cycle, we aim to have a CPU capable of executing a custom instruction set, supported by RAM and a programmable ROM.

### **Core Features**
* **8-Bit Architecture:** Standard 8-bit data bus for arithmetic and logic operations.
* **Modular Design:** Separate modules for the ALU (Arithmetic Logic Unit), Registers, Control Unit, and Memory.
* **Programmable:** A ROM module that can be "flashed" with custom programs using Litematica or in-game tools.
* **High-Performance Hosting:** Hosted on a dedicated **Mac Mini M4** via Docker for maximum tick-rate stability.

---

## 🚀 Getting Started for Members

If you are joining the engineering team, follow these steps to get your environment ready:

1.  **Read the [Setup Guide](./setup.md):** This contains the server IP, the required Mod-stack, and Docker configuration.
2.  **Join the Discord:** All real-time logic debugging and "WorldEdit" sessions are coordinated in the `#mc-cpu-dev` channel.
3.  **Install Litematica:** We use schematics to share circuit designs. Ensure you have the latest blueprints from the `assets/` folder.

---

## 🏗️ Technical Roadmap

### **Phase 1: The ALU (Current)**
* [ ] 8-bit Adder/Subtractor logic.
* [ ] Bitwise operations (AND, OR, XOR, NOT).
* [ ] Flags register (Zero, Carry, Negative).

### **Phase 2: Memory & Registers**
* [ ] 8-byte General Purpose Register file.
* [ ] 64-byte RAM module.
* [ ] Program Counter (PC) logic.

### **Phase 3: Control Unit & Instruction Set**
* [ ] Instruction Decoder.
* [ ] Microcode implementation.
* [ ] Final assembly and "Hello World" program.

---

## 👥 Project Contributors
* **Project Lead:** Yeasin Arafat Rafio
* **Logic Engineers:** [Add Member Name]
* **Infrastructure/SysAdmin:** [Add Member Name]

---
> **Tip:** Use the `/carpet` commands on the server to monitor MSPT (Milliseconds Per Tick). We aim to keep the CPU cycle lag-free even at high clock speeds.