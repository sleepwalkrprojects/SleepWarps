# SleepWarps

A lightweight and intuitive warp management plugin for Minecraft servers featuring a clean GUI interface for effortless teleportation.

## 🎯 Core Features

- **Interactive GUI Menu**: Click-based warp selection using an inventory interface
- **Direct Teleportation**: Quick warp access via command without opening the GUI
- **Persistent Storage**: All warps automatically saved to YAML with full location data
- **Multi-World Support**: Create warps across different worlds with proper world tracking
- **Direction Preservation**: Saves player's viewing direction (yaw/pitch) for precise teleportation
- **Permission System**: Granular control over who can use, create, and delete warps

## 📋 Installation

1. Download the latest release from the [Releases](../../releases) page
2. Place `WarpPlugin-1.0.jar` in your server's `plugins/` folder
3. Restart your server
4. Warps will be stored in `plugins/WarpPlugin/warps.yml`

## 🎮 Commands

| Command | Description | Permission |
|---------|-------------|------------|
| `/warp` | Opens the warp GUI menu | `warp.use` |
| `/warp <name>` | Teleports directly to the specified warp | `warp.use` |
| `/setwarp <name>` | Creates a new warp at your current location | `warp.set` |
| `/delwarp <name>` | Deletes an existing warp | `warp.delete` |

**Aliases**: `/warps` for `/warp`

## 🔐 Permissions

| Permission | Description | Default |
|------------|-------------|---------|
| `warp.use` | Allows using warps | `true` |
| `warp.set` | Allows creating warps | `op` |
| `warp.delete` | Allows deleting warps | `op` |

## 🎨 GUI Interface

The warp menu displays all available warps as **Ender Pearls** in a 27-slot inventory (3 rows):

- **Item**: Ender Pearl with custom name
- **Display Name**: Warp name in gold text
- **Lore**: "Click to warp!" in gray text
- **Click Action**: Instant teleportation to warp location

Example GUI display:
```
╔═══════════════════════════════╗
║        🌀 Warps               ║
╠═══════════════════════════════╣
║ [spawn]  [shop]   [pvp]       ║
║ [nether] [end]    [farm]      ║
║                               ║
╚═══════════════════════════════╝
```

## 📁 Data Storage

Warps are stored in `plugins/WarpPlugin/warps.yml`:

```yaml
spawn:
  world: world
  x: 100.5
  y: 64.0
  z: -200.5
  yaw: 90.0
  pitch: 0.0
  
shop:
  world: world
  x: -450.3
  y: 70.0
  z: 890.7
  yaw: 180.0
  pitch: -15.0
```

### Storage Details

- **Automatic Saving**: Warps save immediately upon creation/deletion
- **World Tracking**: Each warp stores its world name for multi-world compatibility
- **Precision Coordinates**: X, Y, Z stored as doubles for exact positioning
- **View Direction**: Yaw and pitch preserved for consistent player orientation
- **Load on Startup**: All warps automatically loaded when server starts

## 💡 How It Works

### Warp Creation Process

1. **Player Command**: Admin runs `/setwarp <name>` at desired location
2. **Data Capture**: Plugin records:
   - Current world name
   - Precise X, Y, Z coordinates
   - Player's yaw (horizontal rotation)
   - Player's pitch (vertical rotation)
3. **Storage**: Warp saved to `warps.yml` immediately
4. **Confirmation**: Player receives success message

### Teleportation Process

1. **GUI Access**: Player runs `/warp` command
2. **Menu Display**: Inventory opens with all warps as clickable items
3. **Selection**: Player clicks desired warp's Ender Pearl
4. **Validation**: Plugin verifies warp still exists and world is loaded
5. **Teleport**: Player instantly moved to exact warp coordinates with preserved view direction
6. **Feedback**: Success message displayed, inventory closed

## 🔧 Building from Source

### Prerequisites

- Java 17 or higher
- Maven 3.6+

### Build Steps

```bash
git clone https://github.com/yourusername/WarpPlugin.git
cd WarpPlugin
mvn clean package
```

The compiled JAR will be in `target/WarpPlugin-1.0.jar`

## ⚙️ Compatibility

- **Minecraft Version**: 1.19.4+
- **Server Software**: Spigot, Paper, Purpur
- **Java Version**: 17+

Tested and working on Paper 1.19.4, should be compatible with newer versions.

## 📝 Examples

### Creating a Spawn Warp
```
> /setwarp spawn
✓ Warp 'spawn' has been set!
```

### Using the GUI
```
> /warp
[Opens inventory with all warps]
[Click "spawn" ender pearl]
✓ Warped to spawn!
```

### Direct Teleportation
```
> /warp spawn
✓ Warped to spawn!
```

### Deleting a Warp
```
> /delwarp old_location
✓ Warp 'old_location' has been deleted!
```

## 🐛 Known Limitations

- **GUI Capacity**: Maximum 27 warps displayed in the GUI
- **No Pagination**: Warps beyond 27 won't appear in the menu (direct teleport still works)
- **No Categories**: All warps shown in a single list

For larger servers requiring more warps, consider implementing pagination or using direct teleportation commands.

## 📄 License

This project is open source. Feel free to modify, distribute, and use it on your server. No attribution required, but appreciated.

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs via Issues
- Submit pull requests with improvements
- Suggest new features

## ⚠️ Support

If you encounter issues:
1. Verify you're using Minecraft 1.19.4 or newer
2. Ensure Java 17+ is installed
3. Check console for error messages
4. Open an issue with full error details

---

Made for Minecraft server owners who want simple, reliable warp functionality.
