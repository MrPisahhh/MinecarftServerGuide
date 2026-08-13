# Complete Guide to Setting Up a Minecraft Server (For Beginners)

> Author: MakeBy 披萨哈哈哈  
> Target Audience: Complete beginners / server owners who don't know where to start  
> Last Updated: 2026-08-13

---

## 📖 Table of Contents
1. [Choosing a Server Core](#1-choosing-a-server-core)
2. [Sources for Mods and Plugins](#2-sources-for-mods-and-plugins)
3. [Essential Tools for Developers](#3-essential-tools-for-developers)
4. [Writing the Startup Script (.bat)](#4-writing-the-startup-script-bat)
5. [Initial Server Setup](#5-initial-server-setup)
6. [Detailed server.properties Configuration](#6-detailed-serverproperties-configuration)
7. [Login and Connection Methods](#7-login-and-connection-methods)
8. [Properly Shutting Down the Server](#8-properly-shutting-down-the-server)
9. [Installing Plugins / Mods](#9-installing-plugs--mods)
10. [Permission Management (Assigning Permissions to Players)](#10-permission-management-assigning-permissions-to-players)
11. [Regular Backups (Preventing World Corruption)](#11-regular-backups-preventing-world-corruption)
12. [Common Issues and Troubleshooting (Lifesaver for Beginners)](#12-common-issues-and-troubleshooting-lifesaver-for-beginners)
13. [Advanced Tips (Making Your Server More Fun)](#13-advanced-tips-making-your-server-more-fun)
14. [More Community Resources](#14-more-community-resources)
15. [Conclusion](#15-conclusion)

---

## 1. Choosing a Server Core

Choose the core type based on your needs:

| Core Name | Purpose | Download Link |
|-----------|---------|----------------|
| **Spigot** | Plugin server (performance-optimized) | [SpigotMC](https://www.spigotmc.org/) |
| **Paper** | Plugin server (high-performance fork, recommended) | [PaperMC](https://papermc.io/downloads/paper) |
| **Forge** | Mod server (classic) | [Forge Downloads](https://files.minecraftforge.net/net/minecraftforge/forge/) |
| **Fabric** | Mod server (lightweight, modern) | [Fabric Server Launcher](https://fabricmc.net/use/server/) |
| **mohist** | Mod + plugin (not recommended for beginners) | [mohist download](https://www.mohistmc.cn/) |

> 💡 Beginner's advice: Start with a **Paper** plugin server – simple, stable, and with abundant community resources.

---

## 2. Sources for Mods and Plugins

- **Plugins**:
  - [SpigotMC Resources](https://www.spigotmc.org/resources/)
  - [Modrinth (Plugins)](https://modrinth.com/plugin/)
  - [Hangar (PaperMC)](https://hangar.papermc.io/)

- **Mods**:
  - [Modrinth](https://modrinth.com/)
  - [CurseForge](https://www.curseforge.com/)

---

## 3. Essential Tools for Developers

- **GitHub**: [www.github.com](https://github.com/) – The world's code repository; essential for finding plugin source code or learning.
- **Accelerator (recommended)**: Steam++ (Watt Toolkit) [Download](https://steampp.net/) – makes accessing GitHub and foreign websites smoother.
- **IDE (Programming Environment)**:
  - For complete beginners → Recommended: **Trae AI**: [https://www.trae.cn/](https://www.trae.cn/) (smart assistance, quick start)
  - For Java veterans → Recommended: **IntelliJ IDEA**: [Download page](https://www.jetbrains.com/zh-cn/idea/download/?section=windows)
- **Java Environment (required!)**:
  - Cloud download (includes all JDK versions): [Click here](https://1838711787.share.123pan.cn/123pan/SqdGTd-geptv?pwd=MrPS) Password: `MrPS`
  - Recommended: **JDK 17 or 21** (for Minecraft 1.18+ / 1.20+).

---

## 4. Writing the Startup Script (.bat)

**Step 1**: Create a new text file (`.txt`) and rename it to `Start.bat` (make sure the extension becomes `.bat`).  
**Step 2**: Right-click and edit, then paste the following template:

```bat
@echo off
"YourJavaPath\bin\java.exe" -Xms4G -Xmx6G -jar server.jar nogui
pause
```

**Parameter Explanation**:
- `title`: Window title – write whatever you like.
- `-Xms4G`: Minimum allocated memory (in GB) – recommended 2~4G.
- `-Xmx6G`: Maximum allocated memory (in GB) – adjust according to your server's RAM.
- `-jar server.jar`: Core filename – must match the name of the jar you downloaded.
- `nogui`: Does not show Minecraft's built‑in GUI (recommended); remove if you want the GUI.
- `pause`: Keeps the window open so you can see error messages.

> Example (replace with your actual path):
```bat
@echo off
title Minecraft Server BY MrPisahhh 30002
"C:\Java\jdk-21\bin\java.exe" -Xms4G -Xmx6G -jar server.jar nogui
pause
```

---

## 5. Initial Server Setup

1. Place the core file (e.g., `server.jar`) and the startup script `Start.bat` in **the same folder**.
2. **Double-click `Start.bat`** – it will generate a bunch of files and folders (including `eula.txt`).
3. Open `eula.txt`, change `eula=false` to `eula=true` and save (this means you agree to the [Minecraft EULA](https://aka.ms/MinecraftEULA)).
4. **Double-click `Start.bat` again** and wait for the loading to finish, until you see:
   ```
   [Time INFO]: Done (16.302s)! For help, type "help"
   ```
   That means your server has started successfully! 🎉

---

## 6. Detailed server.properties Configuration

This is the core configuration file for your server – open it with Notepad to edit.

> 📌 **Important**: All lines starting with `#` are comments and have no effect – they are only for explanation. Change the parameters below as needed.

| Parameter | Description | Recommended Value |
|-----------|-------------|-------------------|
| `allow-flight` | Whether to allow flying in survival mode | `false` (anti‑cheat) |
| `allow-nether` | Whether to enable the Nether | `true` |
| `broadcast-console-to-ops` | Whether to broadcast console messages to OPs | `true` |
| `difficulty` | Difficulty | `easy` / `normal` / `hard` |
| `enable-command-block` | Whether to allow command blocks | `true` (if needed) |
| `enable-rcon` | Whether to enable remote control | `false` (not recommended for beginners) |
| `enforce-whitelist` | Whether to enforce a whitelist | `false` (can turn off for a friends‑only server) |
| `gamemode` | Default game mode | `survival` / `creative` |
| `generate-structures` | Whether to generate structures (villages, etc.) | `true` |
| `hardcore` | Whether hardcore mode is enabled | `false` |
| `level-name` | The world folder name | `world` (default) |
| `level-seed` | World seed | Leave blank for random |
| `max-players` | Maximum number of players | Set based on server performance |
| `motd` | Server message displayed in the multiplayer server list | `Welcome to my server~` |
| `online-mode` | Whether to enable premium authentication | `true` (premium server) / `false` (offline server) |
| `pvp` | Whether PVP is allowed | `true` |
| `server-port` | Port number | `25565` (default) |
| `view-distance` | Client view distance (in chunks) | `6~10` (lower values improve performance) |
| `simulation-distance` | Simulation distance (in chunks) | `6~8` |
| `spawn-protection` | Spawn protection radius (in blocks) | `16` |

---

## 7. Login and Connection Methods

- **Local login**: Type `127.0.0.1:port` (e.g., `127.0.0.1:25565`).
- **LAN friend connection**:
  - Get your local IP (`ipconfig` in command prompt), then your friend enters `YourLocalIP:port`.
- **External friend connection (public IP)**:
  - Enter your public IP + port directly (requires port forwarding on your router).
- **Intranet penetration (recommended for users without a public IP)**:
  - Use tools like SakuraFrp, Ngrok, etc., and choose TCP protocol.
  - Target IP: fill in `0.0.0.0` or `127.0.0.1`; target port: fill in your `server-port`.
  - After penetration, you will get an external address – send that to your friends.

---

## 8. Properly Shutting Down the Server

**Never click the × on the window directly** – it may corrupt your world!  
Correct method: In the server console, type `stop` and press Enter. Wait for the saving to complete, then the window will close automatically.

---

## 9. Installing Plugins / Mods

### 🔌 Plugins (Paper / Spigot)
1. Download the `.jar` plugin file from the websites mentioned above.
2. Place it into the **`plugins`** folder inside your server folder (create it if it doesn't exist).
3. Restart the server (stop completely and then start) – the plugin will be loaded automatically.
4. The plugin's configuration files will be generated in `plugins/PluginName/` – you can edit them as needed.
5. In the console, type `plugins` and press Enter to see which plugins are enabled (green = enabled, red = disabled, not listed = it wasn't placed correctly).

### 🧩 Mods (Forge / Fabric)
- Forge: Put the mod `.jar` files into the **`mods`** folder, then start the server.
- Fabric: Also put them in `mods`, but you need to install Fabric API and other prerequisite mods first (check the mod page requirements).
- ⚠️ Note: Mod servers require the client to have the same mods installed (both client and server must have them).

---

## 10. Permission Management (Assigning Permissions to Players)

We recommend using the **LuckPerms** plugin (supports all cores).

1. Download LuckPerms and place it in `plugins`, then restart.
2. In the console, type:
   - `/lp creategroup vip` – create a VIP group
   - `/lp group vip permission set essentials.fly` – grant the fly permission to that group (requires EssentialsX)
   - `/lp user PlayerName parent add vip` – add a player to the VIP group
3. For more commands, refer to the [LuckPerms Wiki](https://luckperms.net/wiki).

> For small friend‑only servers, you can simply use `/op PlayerName` to give a player full admin privileges, but be careful – these players can execute `/stop` to shut down the server.

---

## 11. Regular Backups (Preventing World Corruption)

- **Manual backup**: Stop the server, copy the entire server folder (or at least the `world` folder), and rename it to “Backup_Date”.
- **Automatic backup**:
  - Use plugins like [DriveBackupV2](https://www.spigotmc.org/resources/drivebackupv2.100389/) or [Backup](https://www.spigotmc.org/resources/backup.111542/).
  - Or use the system task scheduler to run a `.bat` script that copies the folder at set times.

---

## 12. Common Issues and Troubleshooting (Lifesaver for Beginners)

| Problem | Solution |
|---------|----------|
| **Double‑click .bat and it flashes closed** | Check if the Java path is correct; check if the memory parameters exceed your actual RAM; check if `server.jar` matches the filename. |
| **Error “Java not found”** | Use the absolute path in the .bat (e.g., `"C:\Program Files\Java\jdk-21\bin\java.exe"`). |
| **External players cannot connect** | Check if the firewall has opened the port; check router port forwarding; if using intranet penetration, verify the tunnel address and port. |
| **Error “Failed to bind to port”** | The port is already occupied – close another server or change `server-port`. |
| **Players get version mismatch error** | Ensure the server core version and the client version are exactly the same. |
| **World loading issues or spawn point stuck** | Try deleting the `world` folder to regenerate it (remember to back up first), or check the `level-type` setting. |

---

## 13. Advanced Tips (Making Your Server More Fun)

- **Performance optimisation**: Lower `view-distance` and `simulation-distance`, turn off unused worlds (e.g., `allow-nether=false`).
- **Scheduled restart**: Use the `RestartReboot` plugin or Windows Task Scheduler to restart your server automatically every morning to free up memory.
- **Economy and shops**: Install `PlayerPoint` + `Vault` + `ChestShop` to build an economic system.
- **Anti‑cheat**: `AntiCheatReloaded` or `Matrix`, but watch out for performance overhead. [Not recommended for beginners]
- **Item drops cleanup**: Regularly run `/kill @e[type=!player]` or use a cleanup plugin (e.g., `ClearLag`).
- **Enable RC remote management** (advanced): Set `enable-rcon=true` and set a password, then you can manage the server remotely with third‑party tools.

---

## 14. More Community Resources

- **[MineBBS](https://www.minebbs.com/)** – A large Minecraft community with Java/Bedrock mods and plugins.
- **[GitHub](https://github.com/)** – Numerous Minecraft resources, including open‑source projects like PCL2 and many others.
- **[NameMC](https://www.namemc.com)** – Download skins for premium players.
- **[MSL (Minecraft Server Launcher)](https://www.mslmc.cn/)** – An easier way to set up a server (great for beginners to start with).
- And many more.

---

## 15. Conclusion

You have now mastered all the basic skills to build a Minecraft server from scratch.  
You will definitely run into various errors along the way – don't be afraid. 99% of problems can be solved by searching online or using AI assistants (Doubao, DeepSeek, Qwen, ChatGPT).  


**Wishing your server a booming player base and lots of fun with your friends!** 🎮🍕

---

> 📝 This document was written by MrPisahhh. Feel free to share and modify, but please retain the original author information.  
> If you have questions or additions, please submit an Issue or mrpisahhh@outlook.com.
