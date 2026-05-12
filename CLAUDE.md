# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a minimalist Snake game built with vanilla HTML, CSS, and JavaScript. There is no build system, no package manager, and no external dependencies. Both game and its accompanying documentation are single-file HTML pages that run directly in a browser.

## Project Files

- **snake.html** — The main Snake game. Opens directly in any modern browser.
- **snake_解释.html** — A styled Chinese-language document explaining the code logic line-by-line.
- **README.md** — Project title only (`# claudecodelearn`).

## Architecture

### Game Engine (`snake.html`)

The entire game is self-contained in one HTML file with inline `<style>` and `<script>` tags.

- **Canvas**: 400×400 px grid, divided into 20×20 tiles (`gridSize = 20`).
- **Coordinate System**: Logical grid coordinates (0–19), not pixel coordinates.
- **Game Loop**: `setTimeout(gameLoop, 100)` drives the tick-based update; there is no `requestAnimationFrame`.
- **State**: Mutable variables (`snake`, `food`, `dx`, `dy`, `score`) defined in module scope.
- **Snake Representation**: An array of `{x, y}` objects. Movement uses `unshift(newHead)` + `pop()`. Eating food skips `pop()`, which is how the snake grows.
- **Wall Behavior**: Wrapping (teleport to opposite side).
- **Collision**: Self-collision triggers `resetGame()`.
- **Input**: Arrow keys with anti-reverse guards (e.g., `if (dy !== 1)` before allowing Up).

### Documentation (`snake_解释.html`)

Pure HTML/CSS page with no JavaScript. Contains static Chinese text and code blocks explaining the game logic. Editing it does not affect the game.

## Running the Project

No build or install step is needed.

```bash
# Open the game directly in the default browser
snake.html

# Or serve it locally (optional)
python -m http.server 8080
# Then visit http://localhost:8080/snake.html
```

## Common Tasks

- **Change colors**: Edit `fillStyle` values in `snake.html` — the current palette uses warm neutrals (`#C65A4A` for snake, `#6F655E` for food, `#F7F2EC` for background).
- **Adjust speed**: Change the `100` ms delay in `setTimeout(gameLoop, 100)`.
- **Add features**: The codebase is small enough that any change (e.g., high score, obstacles, speed increase) can be added by modifying `snake.html` directly.
