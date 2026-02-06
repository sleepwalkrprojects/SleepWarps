# SleepWarps

A lightweight warp management plugin for Minecraft servers with a clean GUI interface for teleportation.

## Core Features

- Interactive GUI menu with click-based warp selection
- Direct teleportation via command
- Persistent YAML storage with full location data
- Multi-world support
- Direction preservation (yaw/pitch)
- Granular permission system

## Installation

1. Download the latest release
2. Place `WarpPlugin-1.0.jar` in `plugins/` folder
3. Restart server
4. Warps stored in `plugins/WarpPlugin/warps.yml`

## Commands

| Command | Description | Permission |
|---------|-------------|------------|
| `/warp` | Opens warp GUI | `warp.use` |
| `/warp <name>` | Teleports to warp | `warp.use` |
| `/setwarp <name>` | Creates warp | `warp.set` |
| `/delwarp <name>` | Deletes warp | `warp.delete` |

**Aliases**: `/warps` for `/warp`

## Permissions

| Permission | Description | Default |
|------------|-------------|---------|
| `warp.use` | Use warps | `true` |
| `warp.set` | Create warps | `op` |
| `warp.delete` | Delete warps | `op` |

## GUI Interface

Warps display as Ender Pearls in a 27-slot inventory. Click to teleport instantly.

## Data Storage

Warps stored in `plugins/WarpPlugin/warps.yml`:

```yaml
spawn:
  world: world
  x: 100.5
  y: 64.0
  z: -200.5
  yaw: 90.0
  pitch: 0.0
```

All warps save immediately and load automatically on server start.

## Building from Source

Requires Java 17+ and Maven 3.6+

```bash
git clone https://github.com/yourusername/WarpPlugin.git
cd WarpPlugin
mvn clean package
```

Output: `target/WarpPlugin-1.0.jar`

## Compatibility

- **Minecraft**: 1.19.4+
- **Server**: Spigot, Paper, Purpur
- **Java**: 17+

## Examples

```
> /setwarp spawn
Warp 'spawn' has been set!

> /warp
[Opens GUI with all warps]

> /warp spawn
Warped to spawn!

> /delwarp noah
Warp 'noah' has been deleted!
```

## Known Limitations

- Maximum 27 warps in GUI (no pagination)
- No warp categories
- Direct commands work beyond 27 warps

## License

Open source. Modify and distribute freely.

## Contributing

Contributions welcome via issues and pull requests.
ests.

## Support

For issues, verify Minecraft 1.19.4+ and Java 17+, then check console errors.

---

Simple, reliable warp functionality for Minecraft servers.
