Setup Stpes for Rafio Minecraft Server Setup

---

## 1. The Mod List (The Hardware Stack)

We will use **Minecraft 1.21.1** as our base version. It is the gold standard for technical mods in 2026.

### Phase 1: Core Engineering (Install Now)
| Mod Name | Side | Purpose |
| :--- | :--- | :--- |
| **Fabric API** | Both | The essential "engine" that lets mods talk to each other. |
| **MaLiLib** | Client | Library required specifically for Litematica to function. |
| **Litematica** | Client | Schematic "ghost" blueprints and material checklists. |
| **Carpet Mod** | Both | Control tick rates (`/tick freeze`), TPS monitoring, and logic fixes. |
| **Sodium** | Client | **Crucial for M4.** Rewrites the render engine for massive FPS on macOS. |
| **Lithium** | Server | Optimizes the game's internal physics and ticking logic. |
| **Redstone Tweaks** | Client | (Resource Pack) Shows signal strength on dust and observer directions. |

### Phase 2: Scaling Up (Install Later)
* **Axiom (Client):** For when you need to "drag and drop" entire sections of the CPU.
* **WorldEdit (Both):** For bulk commands like `//replace iron_block gold_block`.
* **Redstone Multimeter (Both):** A digital oscilloscope to see the exact game tick a signal fires.

---

## 2. The Server Schematic (`docker-compose.yml`)

Create a folder on your Mac named `mc-server`. Inside, create a file named `docker-compose.yml`. Use this exact configuration to leverage your M4's ARM architecture:

```yaml
services:
  minecraft-cpu-server:
    image: itzg/minecraft-server:latest
    container_name: redstone-host
    tty: true
    stdin_open: true
    ports:
      - "25565:25565"
    environment:
      EULA: "TRUE"
      TYPE: "FABRIC"
      VERSION: "1.21.1"
      MEMORY: "8G" # M4 handles this easily
      # Performance tweaks for ARM64/Apple Silicon
      JVM_OPTS: "-XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1"
    volumes:
      - ./data:/data
    restart: unless-stopped
```

---

## 3. The Setup Guide

### Part A: Client Setup (SKLauncher)
1.  **Create Profile:** Open SKLauncher -> New Installation -> Version: **Fabric 1.21.1**.
2.  **Locate Mods Folder:** Click the three dots (⋮) on the profile -> **Open Directory**. Create a folder named `mods`.
3.  **Install Files:** Drop the `.jar` files for **Fabric API, MaLiLib, Litematica, Carpet, Sodium,** and **Lithium** into that folder.
4.  **Resource Pack:** Drop the **Redstone Tweaks** `.zip` into the `resourcepacks` folder. Activate it in-game via *Options > Resource Packs*.

### Part B: Server Setup (Docker)
1.  **Run Docker:** Open Terminal, `cd` into your `mc-server` folder, and run:
    `docker-compose up -d`
2.  **Install Server Mods:** Once the `data` folder appears, go to `data/mods` and drop **Fabric API, Carpet Mod,** and **Lithium** there.
3.  **Restart:** Run `docker-compose restart` to load the mods.

---

## 4. Operational "Cheat Sheet"

| Action | Command / Key |
| :--- | :--- |
| **Open Litematica Menu** | `M` |
| **Open Litematica Config** | `M + C` (Go here to change hotkeys) |
| **Load a Schematic** | `M -> Load Schematics` |
| **Freeze Time (Carpet)** | `/tick freeze` (Great for seeing signal propagation) |
| **Advance 1 Game Tick** | `/tick step 1` |
| **Verify Build** | `M + V` (Shows if you placed a repeater wrong) |
