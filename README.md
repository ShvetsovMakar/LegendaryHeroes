# Legendary Heroes 👾

A procedurally generated dungeon-crawling RPG built with PyGame. Create a character, explore a dynamic forest, battle enemies, collect loot, and face tactical combat challenges in this turn-based adventure.

## 🎮 Features

- **Character Creation & Progression** - Create unique heroes with customizable names and appearance
- **Dynamic Level Generation** - Procedurally generated forest levels ensure every playthrough is unique
- **Turn-Based Combat** - Engage in strategic battles against various enemy types
- **Inventory & Gear System** - Equip helmets, breastplates, and leggings to enhance stats
- **NPCs & Dialogue** - Interact with merchants and warriors in the central lobby
- **Save System** - Persistent character data between sessions
- **Fullscreen Experience** - Immersive gameplay optimized for modern displays

## 🚀 Quick Start

### Prerequisites

- **Python 3.7+**
- **pip** (Python package manager)

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/ShvetsovMakar/LegendaryHeroes.git
   cd LegendaryHeroes
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

### Running the Game

**Option 1: Run from source (Recommended for development)**
```bash
python main.py
```

**Option 2: Use the compiled executable**
```bash
./game.exe
```

## 📖 How to Play

### Main Menu
- **Play** - Choose an existing character to start your adventure
- **Add Character** - Create a new hero with a custom name and appearance
- **Exit** - Close the game

### Creating a Character
1. Click **Add Character**
2. Select a character appearance using the arrow buttons (Guts, Witcher, Kratos, or Griffith)
3. Enter a unique character name
4. Click **Create Character** to save

### Gameplay

#### Lobby
- Start in a peaceful lobby where you can interact with NPCs
- Click on **Merchant** to trade or manage inventory
- Click on **Warrior** for tips and guidance
- Click on a highlighted tile to move there
- Press **ESC** to return to the main menu

#### Combat
- Click tiles to navigate your character through procedurally generated forests
- Enemies spawn automatically and will chase you
- Combat is automatic when enemies move adjacent to you
- Your agility and gear protection determine your survival chance
- Defeat all enemies to complete the level and earn gold
- Press **ESC** to return to the lobby

#### Gear System
- **Helmet** - Increases agility (dodge chance)
- **Breastplate** - Provides protection (damage reduction)
- **Leggings** - Enhances defense stats
- Equip better gear to survive harder battles

### Game States

| Screen | Description |
|--------|-------------|
| Main Menu | Start point of the game with navigation options |
| Add Character | Character creation interface |
| Choose Character | Select which character to play |
| Lobby | Central hub connecting to battles |
| Battle Map | Procedurally generated combat arena |
| Battle Ending | Victory screen showing gold collected |
| Defeat | Game Over screen when health reaches 0 |

## 📁 Project Structure

```
LegendaryHeroes/
├── main.py                      # Core game engine and main loop
├── requirements.txt             # Project dependencies
├── game.exe                     # Compiled Windows executable
├── Config/                      # Configuration and game constants
│   ├── constants.py            # Game settings and parameters
│   └── Maps/                   # Map layout files
│       └── lobby.txt          # Lobby layout template
├── Data/                        # Game data and persistence
│   ├── Characters/            # Character save files (JSON)
│   └── CurrentCharacter/      # Currently selected character data
├── Sprites/                     # Game objects and UI elements
│   ├── Player/                # Player character implementation
│   │   └── Player.py         # Player class with stats and gear
│   ├── Mobs/                  # Non-player characters
│   │   ├── Enemy.py          # Enemy type with combat logic
│   │   ├── Merchant.py       # Merchant NPC
│   │   ├── Warrior.py        # Warrior NPC
│   │   └── Forester.py       # Forest boss
│   ├── Button.py              # Interactive button class
│   ├── Label.py               # Static image/text display
│   ├── TextBox.py             # Text rendering
│   ├── InputBox.py            # User input field
│   └── Tile.py                # Walkable/blocking tiles
├── OnClickFunctions/           # Event handlers for buttons
│   ├── on_click_main_menu.py
│   ├── on_click_add_character.py
│   ├── on_click_choose_character.py
│   ├── on_click_to_main_menu.py
│   └── on_click_battle_ending.py
├── Graphics/                   # Visual assets
│   ├── MainMenu/              # Main menu UI graphics
│   ├── Characters/            # Character sprites
│   ├── Enemies/               # Enemy sprites and animations
│   ├── Villagers/             # NPC sprites
│   ├── Tiles/                 # Terrain sprites
│   └── Icon/                  # Application icon
├── Sprites/                   # Sprite graphics
│   ├── Enemies/              # Enemy animation frames
│   └── Characters/           # Character animations
├── Fonts/                      # Custom fonts (Norse font family)
└── .idea/                      # IDE configuration files
```

## 🎯 Game Mechanics

### Character Stats

| Stat | Description | Effect |
|------|-------------|--------|
| Health | Hit points remaining | Game Over if reaches 0 |
| Agility | Dodge chance percentage | Higher = more damage avoidance |
| Protection | Damage reduction multiplier | Reduces incoming damage |
| Gold | Currency collected in battles | Used for transactions |

### Combat System

- **Evasion** - Your agility is compared against a random number (1-100)
- **Damage Calculation** - `Incoming Damage × (1 - Protection)`
- **Enemy AI** - Enemies move randomly towards walkable tiles, avoiding obstacles
- **Victory Condition** - Survive and eliminate all enemies to proceed

### Procedural Generation

The forest map generator creates unique layouts using:
- **Main Path** - A guaranteed walkable route through the level
- **Sub-Paths** - 64 branching paths for exploration
- **Obstacles** - Random trees and stones blocking movement
- **Guaranteed Exploration** - Multiple routes to the forest boss

## 🛠️ Technical Details

### Architecture

- **Camera System** - Smooth viewport following the player character
- **Sprite Groups** - Efficient rendering using PyGame sprite groups
- **Event-Driven** - Click-based movement and interaction system
- **JSON Persistence** - Character data saved in JSON format
- **Fullscreen Display** - Automatic resolution detection

### Performance

- **FPS Control** - Capped at 60 FPS for smooth gameplay
- **Collision Detection** - Tile-based movement prevents overlapping
- **Asset Caching** - Graphics loaded once at startup

## 📦 Dependencies

- **pygame** (v2.6.1) - Game engine and rendering
- **PyTMX** (v3.32) - Tiled map support
- **PyInstaller** - Used to compile the `.exe` executable

See `requirements.txt` for the complete dependency list.

## 🎓 Educational Context

This project was created as a learning exercise for **Yandex Lyceum**, demonstrating:
- Object-oriented game development
- Event-driven architecture
- Procedural generation algorithms
- State management in games
- Asset handling and resource management

## 💡 Development Tips

### Debugging

Enable debug info by modifying constants in `Config/constants.py`:
```python
DEBUG = True  # Shows collision boxes and tile info
```

### Adding New Enemy Types

1. Create a new class in `Sprites/Mobs/`
2. Inherit from `Enemy` base class
3. Add sprites to `Graphics/Enemies/[YourEnemy]/`
4. Register in combat spawner with health and damage values

### Modifying Level Generation

Edit `Map.generate_forest()` in `main.py` to adjust:
- `field_width` and `field_height` - Map dimensions
- `sub_paths_amount` - Number of branching paths
- `obstacle_types` - Terrain block distribution

## 🐛 Known Issues

- Screen resolution detection works best on 16:9 displays
- Performance may vary on lower-end systems with complex forest generation

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs via GitHub Issues
- Suggest features for enhancement
- Submit pull requests with improvements

## 📜 License

This project is provided as-is for educational purposes. See your institution's guidelines for usage and modification rights.

## 📞 Contact

Created by [@ShvetsovMakar](https://github.com/ShvetsovMakar)

For questions or issues, please open a GitHub issue in this repository.

---

**Ready for adventure? Download or clone the repo and start playing!** 🎮⚔️
