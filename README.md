# Sun-Wu-Kuo

**A 2D action RPG inspired by the legend of Sun Wukong, developed in C++17 with Allegro 5.**

![C++17](https://img.shields.io/badge/C%2B%2B-17-00599C) ![Allegro 5](https://img.shields.io/badge/Allegro-5-555555) ![CMake](https://img.shields.io/badge/Build-CMake-064F8C)

Sun-Wu-Kuo is a collaborative game-development project that brings together object-oriented programming, real-time gameplay, animation, and a scene-based application architecture. The project explores how to organize a larger C++ codebase into reusable systems for game logic, rendering, user interfaces, and player interaction.

## Features

- **Action RPG gameplay:** Player movement and combat, enemies and bosses, collision handling, maps, and stage progression.
- **Game progression:** Coins, a shop system, stage selection, and win/lose scenes.
- **Visuals and audio:** Sprite animation, parallax backgrounds, visual effects, sound, dialogue, and story scenes.
- **Menus and settings:** Start screen, pause/settings controls, and supporting UI components.
- **Account and social interfaces:** Login and signup scenes, leaderboard, friend list, search, requests, and chat-related components. Some online functionality may depend on external services or configuration.

## Tech Stack

| Technology | Purpose |
| --- | --- |
| **C++17** | Gameplay systems and object-oriented application logic |
| **Allegro 5** | Rendering, input, audio, and multimedia functionality |
| **CMake** | Project configuration and compilation |
| **libcurl** | Networking-related functionality |

## Software Design

The codebase separates responsibilities across dedicated modules rather than keeping gameplay logic in a single file.

```text
Sun-Wu-Kuo/
├── Engine/       # Game loop, scenes, objects, rendering helpers, collision, audio
├── Scene/        # Gameplay, menus, story, login, leaderboard, and social scenes
├── Player/       # Player behavior, animations, and coin-related code
├── Enemy/        # Enemy and boss implementations
├── Shop/         # Shop and item systems
├── UI/           # UI controls and visual effects
├── Resource/     # Images, fonts, audio, and other resources/dependencies
├── main.cpp      # Scene registration and game startup
├── CMakeLists.txt
└── Makefile
```

### Object-oriented architecture

- **Scene abstraction:** Scenes follow the `Engine::IScene` interface, separating initialization, updates, rendering, and event handling.
- **Inheritance and polymorphism:** Specialized scene classes implement common scene behavior through overrides.
- **Modular systems:** Player, enemies, UI elements, and engine utilities are organized into separate classes and source files.
- **Scene management:** `main.cpp` registers the game's screens with `Engine::GameEngine`, which starts the application.

This structure made it possible to work on gameplay, presentation, and supporting interfaces as distinct parts of a shared project.

## Building and Running

### Requirements

- A **C++17-compatible compiler**
- **CMake 3.27 or later**
- **Allegro 5** with the relevant addons
- The **libcurl** headers and libraries referenced by the project

> **Platform note:** The current CMake configuration is Windows-oriented. On Windows, it expects Allegro headers and libraries under `C:/allegro/include` and `C:/allegro/lib`, plus the included/expected DLL dependencies. The executable target is currently named `2025_I2P2_TowerDefense`. These are existing project settings, not the repository name. Other operating systems may require dependency and linker changes.

### Build on Windows (MinGW toolchain)

1. Install a compatible C++ toolchain and CMake; configure Allegro 5 at the paths noted above.
2. Clone the repository and configure the build:

   ```powershell
   git clone https://github.com/BryanGilbert-T/Sun-Wu-Kuo.git
   cd Sun-Wu-Kuo
   cmake -S . -B build -G "MinGW Makefiles"
   ```

3. Build the project:

   ```powershell
   cmake --build build --config Debug
   ```

4. From the repository root, try launching the generated executable:

   ```powershell
   .\build\2025_I2P2_TowerDefense.exe
   ```

The game requires its assets and runtime libraries to be accessible at runtime. If the build or launch fails, check the Allegro installation, libcurl import library, DLL availability, and the working directory used for resource paths.

**Build status:** These instructions reflect the checked-in CMake configuration; a clean-machine build has not been independently verified.

## Project Context and Credits

This project was developed collaboratively as an academic game-development project. The repository's original contribution notes identify the following areas of work:

- **蔡文鎮:** Game structure and audio (50%).
- **楊愛玉:** Graphics design and animation (50%).

The project uses Allegro 5 and includes game assets and third-party dependencies. Please review the applicable licenses or permissions before redistributing those materials.

## Gameplay Preview

Gameplay screenshots or a short GIF can be added here to show the combat, menus, and animation systems. Keeping media in a `docs/` folder can help make this README easier to maintain.

---

*Built to explore C++ game development, object-oriented design, and collaborative software engineering.*
