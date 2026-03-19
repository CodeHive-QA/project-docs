## ⚙️ Infrastructure & Environment Setup

The development of the **CodeHive CPU Project** is divided into two distinct stages to ensure stability before adding advanced debugging tools.

  * **Phase 1 (Initial):** Core logic building and basic server stability.
  * **Phase 2 (Advanced):** High-frequency debugging, frame-perfect multimeters, and bulk data-bus cloning.

-----

## 🏗️ Server-Side Configuration (Admins)

The Minecraft server is the "Central Processing Unit" of our project. It runs in a containerized environment to ensure high-frequency Redstone calculations remain consistent.

### **Requirements & Environment**

  * **Hardware:** Recommended **6GB+ RAM** to prevent tick-skip during large logic updates.
  * **World Settings:** Creative Mode, Flat World, No Mob Spawning.
  * **Deployment:** Managed via **Docker**. For those preferring a GUI, **SquidServer** is a compatible alternative.
  * **Networking:** Currently utilizing **playit.gg** for tunneling.
    > **Note:** We will transition to direct **Port Forwarding** in Phase 2 for reduced latency.

### **Server Orchestration**

The configuration is maintained in our `docker-compose` file.

  * **Config File:** [`./assets/minecraft-server.yml`](./assets/minecraft-server.yml){:download="docker-compose.yml"}

### **Primary Server Mods**

| Mod | Phase | Purpose |
| :--- | :--- | :--- |
| **Fabric API** | P1 | Essential hook for all server-side mods. |
| **Lithium** | P1 | Physics and game-loop optimization. |
| **Carpet Mod** | P1 | Tick-rate control and performance monitoring. |
| **WorldEdit** | P1 | Rapid prototyping and structure manipulation. |

-----

## 🎮 Client-Side Setup (Players)

To connect to the CodeHive cluster, players must configure their local Minecraft installation to match our Fabric environment.

### **Launcher & Version**

  * **Recommended Launcher:** [SKLauncher](https://sklauncher.pl/) (allows for easy modpack management).
  * **Minecraft Version:** **1.21.1**
  * **Mod Loader:** Fabric

### **Installation Methods**

1.  **Manual / SKLauncher:** Go to `Installation Manager` \> `Modpacks`. Search and add the required mods listed below.
2.  **Quick Setup:** Download the [**Client Mod-Stack v0.1**](./assets/client-mods-v0.1.zip){:download="client-mods-p1.zip"} and extract it into your `.minecraft/mods` folder.

### **Essential Client Mods**

  * **Fabric API:** Core dependency.
  * **MaLiLib:** Library required for Litematica.
  * **Litematica:** For viewing CPU logic blueprints and schematics.
  * **Sodium:** Drastic FPS improvements when viewing large-scale Redstone builds.

### **Visual Support**

Upon joining the server, you will receive an automatic prompt to download the **Redstone Tweaks** resource pack.

  * **Required:** Yes.
  * **Function:** Visualizes wire signal strengths (0–15) and directional pulse indicators, which are critical for debugging logic gates.


## All Mods List

This is the master list for the **CodeHive CPU Project**. It is categorized by phase to ensure we don't overload the server or clients during the initial build.

| Mod Name | Phase | Side | Function |
| :--- | :---: | :---: | :--- |
| **Fabric API** | P1 | Both | Core library required for all mods to function. |
| **MaLiLib** | P1 | Client | Library mod required for Litematica's UI and configs. |
| **Litematica** | P1 | Client | Provides holograms/schematics for building CPU components. |
| **Carpet Mod** | P1 | Both | Allows `/tick` control, fake players, and TPS/MSPT monitoring. |
| **Lithium** | P1 | Server | Optimization for physics and game-loop logic. |
| **Sodium** | P1 | Client | Massive FPS engine overhaul; essential for large Redstone builds. |
| **WorldEdit** | P1 | Both | Enables bulk cloning, rotating, and moving of large logic buses. |
| **Redstone Tweaks** | P1 | Client | **(Resource Pack)** Visualizes power levels (0-15) on wires. |
| **RS Multimeter** | P2 | Both | Frame-perfect logic debugging and pulse capturing. |
| **Axiom** | P2 | Client | Professional-grade tool for world manipulation and 3D logic. |
| **Iris Shaders** | P2 | Client | Used for high-quality cinematic recordings of the finished CPU. |

---

### **Installation Breakdown**

* **Server-Side:** These are installed in the Docker container (`./assets/minecraft-server.yml`). They ensure the world stays lag-free and supports our logic tools.
* **Client-Side:** These go in your local `mods` folder. If you are using **SKLauncher**, you can manually add these via the *Installation Manager* or use our pre-built zip.
* **Both:** These mods must be present on both the server and your computer for the features (like WorldEdit commands or Multimeter data) to sync properly.

**Would you like me to update the "Quick Start" section to include specific instructions for the Phase 2 mods?**