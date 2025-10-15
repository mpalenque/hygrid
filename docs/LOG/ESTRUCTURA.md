# 📁 Folder Structure - Tetris Game

## 🎯 New Organization

The application is now organized in a professional modular structure:

```
clean/
├── index.html                    # Main HTML file
├── README.md                     # Main documentation
│
├── src/                          # Source code
│   ├── main.js                   # Application entry point
│   ├── core/                     # Main classes
│   │   ├── App.js               # Main application (THREE.js setup)
│   │   └── TetrisGame.js        # Tetris game logic
│   │
│   ├── scenes/                   # 3D scenes
│   │   └── IdleScene.js         # Floating cubes scene
│   │
│   └── managers/                 # Game managers
│       └── GameStateManager.js   # Game states (idle, intro, playing, etc.)
│
├── assets/                       # Game resources
│   ├── images/                   # Images and textures
│   │   ├── cube.png             # Cube texture
│   │   ├── logo.png             # Main logo
│   │   ├── union-logo-full.svg
│   │   ├── union-logo-filled.svg
│   │   └── union-logo-outline.svg
│   │
│   └── audio/                    # Audio and music
│       └── midiplayer/          # MIDI system
│           ├── dance.mid
│           ├── MIDIFile.js
│           ├── MIDIPlayer.js
│           └── WebAudioFontPlayer.js
│
└── docs/                         # Documentation
   └── LOG/                     # History and backups
```

## 📦 Module Structure

### 1. **src/main.js** (Entry Point)
```javascript
import { App } from './core/App.js';
new App();
```
- Simple file that starts the entire application
- Single entry point imported by `index.html`

### 2. **src/core/App.js** (Main Application)
```javascript
import { TetrisGame } from './TetrisGame.js';
import { IdleScene } from '../scenes/IdleScene.js';
import { GameStateManager } from '../managers/GameStateManager.js';
```
- Configures THREE.js (scene, camera, renderer, lights)
- Orchestrates all main classes
- Handles the main animation loop

### 3. **src/core/TetrisGame.js** (Game Logic)
- Board and pieces system
- Collision detection
- Scoring and level system
- Yellow power-up mode
- Visual effects

### 4. **src/scenes/IdleScene.js** (Idle Scene)
- Animated floating cubes
- 3D grid system
- Camera effects

### 5. **src/managers/GameStateManager.js** (States)
- State machine (idle → intro → playing → gameover)
- Scoreboard system
- Screen transitions

## 🔗 Import System

### Relative Paths:
- `src/main.js` → `./core/App.js`
- `App.js` → `./TetrisGame.js` (same directory)
- `App.js` → `../scenes/IdleScene.js` (up and down)
- `App.js` → `../managers/GameStateManager.js` (up and down)

### Asset Paths:
- Textures: `../../assets/images/cube.png`
- HTML Images: `assets/images/logo.png`
- Audio: `./assets/audio/midiplayer/dance.mid`
- MIDI Scripts: `./assets/audio/midiplayer/MIDIPlayer.js`

## ✅ Advantages of This Structure

### 1. **Separation of Concerns**
- **core/**: Main game logic
- **scenes/**: Independent 3D scenes
- **managers/**: State and flow managers
- **assets/**: Resources separated from code

### 2. **Easy Navigation**
- Quickly find what you're looking for
- Descriptive folder names
- Clear and logical hierarchy

### 3. **Scalability**
```
src/
├── core/
│   ├── App.js
│   ├── TetrisGame.js
│   └── PieceFactory.js        ← Easy to add more
├── scenes/
│   ├── IdleScene.js
│   └── GameScene.js           ← New scenes
├── managers/
│   ├── GameStateManager.js
│   ├── ScoreManager.js        ← New managers
│   └── AudioManager.js
└── utils/                      ← New utilities folder
    ├── constants.js
    └── helpers.js
```

### 4. **Maintenance**
- Smaller, focused files
- Localized changes (don't affect everything)
- Easier testing by modules

### 5. **Collaboration**
- Multiple developers can work without conflicts
- Clearer git diffs
- More effective code reviews

## 🚀 Migration from Previous Version

### Before:
```html
<script type="module" src="./game.js"></script>
```

### Now:
```html
<script type="module" src="./src/main.js"></script>
```

## 📋 Verification Checklist

- ✅ `src/main.js` correctly imports from `src/core/App.js`
- ✅ `App.js` imports from `src/core/`, `src/scenes/`, `src/managers/`
- ✅ Textures load from `assets/images/`
- ✅ MIDI audio loads from `assets/audio/midiplayer/`
- ✅ HTML images load from `assets/images/`
- ✅ MIDI scripts load from `assets/audio/midiplayer/`
- ✅ index.html points to `src/main.js`

## 🎯 Suggested Next Improvements

1. **Create constants.js**
   - Colors, dimensions, configurations
   - Centralize magic values

2. **Create PieceFactory.js**
   - Separate piece definitions
   - Make it easier to add new pieces

3. **Create AudioManager.js**
   - Encapsulate all MIDI logic
   - Simplify HTML

4. **Add utils/**
   - Reusable helper functions
   - Mathematical helpers

5. **Consider types/ or interfaces/**
   - If you decide to use TypeScript later
   - Type documentation

## 💡 Development Tips

### Open in VS Code:
```bash
cd /Users/mpalenque/tetrisclean/clean
code .
```

### Live Server:
- Install "Live Server" extension in VS Code
- Right-click on `index.html` → "Open with Live Server"

### Debug:
- 404 errors: Check relative paths
- Import errors: Check `.js` extension in imports
- Textures not loading: Check paths from current module

## 📞 Support

Problems with paths?
1. Check browser console
2. Review relative paths in imports
3. Confirm assets/ is in the right place
4. Use DevTools → Network to see which files fail

---

**The application is ready to use with the new modular structure!** 🎮✨
