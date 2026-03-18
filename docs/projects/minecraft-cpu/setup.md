# ⚙️ Infrastructure & Environment Setup

## 🏗️ Server Architecture (Admins)
The minecraft server runs on a **beefy computer** inside Docker to handle high-frequency Redstone calculations.

### **Docker Compose**
```yaml
services:
  mc-server:
    image: itzg/minecraft-server
    container_name: codehive_mc_cpu
    environment:
      EULA: "TRUE"
      TYPE: "FABRIC"
      MEMORY: "8G"
    ports:
      - "25565:25565"
    volumes:
      - minecraft-cpu:/data
    restart: unless-stopped

  # optional: use tunneling if port forwarding is unavailable
  playit-tunnel:
    image: itzg/playit
    environment:
      SECRET_KEY: "your_secret_key"
    restart: unless-stopped

volumes:
  minecraft-cpu:
```

---

## 🎮 Client Configuration (Players)
* **Launcher:** Any minecraft launcher will work but we recommend [SKLauncher](https://sklauncher.pl/)
* **Version:** Fabric (Latest 1.21.x)
* **RAM:** Allocate **4GB+** in launcher settings.

### **Required Mod-Stack**

| Mod | Side | Description |
| :--- | :--- | :--- |
| **Fabric API** | Both | Core library for all mods. |
| **Litematica** | Client | CPU logic blueprints/schematics. |
| **Carpet Mod** | Both | Tick-rate control and MSPT monitoring. |
| **Sodium** | Client | Optimization for high-FPS logic viewing. |
| **Lithium** | Server | Physics and tick-loop optimizations. |
| **Redstone Tweaks**| Client | Visualizes wire signal strength (0-15). |
| **Axiom** (P2) | Client | Advanced structural/logic building. |
| **WorldEdit** (P2)| Both | Bulk cloning of data buses/memory. |
| **RS Multimeter** (P2)| Both | Frame-perfect clock cycle debugging. |

!!! info 

    P2 means Phase 2. 
    We would install and use those in later development phase

---

## 🛠️ Quick Start
1. **Mods:** Download the `.zip` from Discord and import into SKLauncher.
2. **Schematics:** Place `.litematic` files in `/.minecraft/schematics/`.
3. **Connect:** Use the IP provided in the `#mc-cpu-dev` channel.

