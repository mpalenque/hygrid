# 🎮 Tetris Game - Standalone Version with Three.js

## 📋 Description
Completely autonomous version of Tetris game using pure Three.js (no Needle Engine).

## 🚀 How to run

### Option 1: Live Server (VS Code)
1. Open VS Code
2. Open the file: `/clean/index.html`
3. Right-click → "Open with Live Server"
4. The game will open in your browser

### Option 2: Direct browser
1. Navigate to the `/clean` folder
2. Open `index.html` directly in your browser
3. ⚠️ **IMPORTANT**: Some browsers block ES6 modules for security. If you see CORS errors, use Live Server.

### Option 3: Simple HTTP server
```bash
cd /Users/mpalenque/Desktop/Unitytetris/Needle/newProject/clean
python3 -m http.server 8000
```
Then open: http://localhost:8000

## 🎯 Controls

- **⬅️ Left arrow**: Move piece left
- **➡️ Right arrow**: Move piece right
- **⬇️ Down arrow**: Accelerate fall
- **⬆️ Up arrow / Space**: Rotate piece
- **Any key**: Start game from IDLE screen

## 🎮 Game mechanics

### Objective
Place colored pieces in their corresponding zones:
- 🔴 **Red Zone** (columns 0-3): Red pieces/blocks
- 🔵 **Blue Zone** (columns 4-7): Blue pieces/blocks
- 🟢 **Green Zone** (columns 8-11): Green pieces/blocks

### Pieces
- Pieces of 2, 3 and 4 blocks
- Some pieces have multiple colors
- Multi-color pieces can fit in different zones

### Scoring system
- **100 points** for each correctly completed section
- **Level**: Goes up every 10000 points
- **Speed**: Increases 15% per level
- **Modo Bonus**: Se activa cada 10000 puntos durante 5 segundos

### Modo Bonus 🟡
Cuando alcanzas cada 10000 puntos:
- Todas las piezas se vuelven amarillas
- Puedes colocar cualquier pieza en cualquier zona
- Dura 5 segundos
- ¡Aprovecha para completar más líneas!

## 📁 Estructura de archivos

```
/clean/
├── index.html              # Archivo principal (ABRE ESTE)
├── game.js                 # Lógica del juego con Three.js
├── union-logo-outline.svg  # Logo base
├── union-logo-filled.svg   # Logo con color
└── midiplayer/             # Reproductor de música MIDI
    ├── dance.mid
    ├── MIDIFile.js
    ├── MIDIPlayer.js
    └── WebAudioFontPlayer.js
```

## 🎵 Audio

### Música
- Música de fondo en formato MIDI
- Se inicia automáticamente al comenzar el juego
- Tempo se ajusta con el nivel

### Efectos de sonido (8-bit)
- ✅ Completar línea: "Truin!" (3 notas ascendentes)
- ⭐ Entrar en bonus: Chime brillante
- 💎 Alcanzar bonus: Power-up
- 📈 Subir nivel: Fanfare

## 🖥️ Estados del juego

1. **IDLE**: Pantalla de inicio
   - Presiona cualquier tecla para jugar
   - Muestra scoreboard cada 10 segundos

2. **INTRO**: Countdown 5-4-3-2-1-GO!

3. **PLAYING**: Juego activo
   - Header con nivel y zonas
   - Footer con puntuación y logo
   - Indicador de bonus cuando está activo

4. **GAME OVER**: Pantalla final
   - Muestra puntuación y líneas
   - Guarda en scoreboard
   - Vuelve a IDLE después de 5 segundos

## 🏆 Scoreboard

- Se guardan los últimos 10 puntajes
- Almacenado en localStorage del navegador
- Se muestra automáticamente cada 10 segundos en IDLE
- Ordenado de mayor a menor puntaje

## ⚙️ Tecnologías

- **Three.js** (desde CDN): Motor 3D
- **Vanilla JavaScript**: Lógica del juego
- **Web Audio API**: Efectos de sonido
- **MIDI Player**: Música de fondo
- **LocalStorage**: Guardar puntajes

## 🎨 Diseño

Todos los colores y diseño son idénticos al original:
- Amarillo: `#dcee2d`
- Rojo: `#cf4526`
- Azul: `#21b1f8`
- Verde: `#47ebcd`
- Gris: `#656565`

## 🐛 Solución de problemas

### El juego no carga
- Asegúrate de abrir `/clean/index.html` (no el root del proyecto)
- Usa Live Server o un servidor HTTP local
- Verifica que tienes conexión a internet (Three.js se carga desde CDN)

### No se ve el logo
- Los archivos SVG deben estar en la misma carpeta que index.html
- Verifica que `union-logo-outline.svg` y `union-logo-filled.svg` existen

### No hay música
- La música se carga desde `./midiplayer/dance.mid`
- Asegúrate de que la carpeta `midiplayer` está completa
- Haz click en la página para activar el AudioContext (requerimiento del navegador)

### Errores de CORS
- No abras el archivo directamente (file://)
- Usa Live Server o un servidor HTTP local

## 📝 Notas

- El juego se escala automáticamente para adaptarse a cualquier tamaño de ventana
- Proporción fija: 1166x1920 (formato vertical)
- Totalmente funcional sin dependencias externas (excepto Three.js desde CDN)
- No requiere build ni compilación

¡Disfruta del juego! 🎮✨
