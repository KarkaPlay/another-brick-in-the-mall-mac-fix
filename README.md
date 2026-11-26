# Another Brick in the Mall — Apple Silicon Fix

An unofficial compatibility fix for running Another Brick in the Mall on Apple Silicon Macs using CrossOver and WineMetalGL.

## Fixed issues

- Startup crash caused by a GLSL shader compilation error.
- Extremely low in-game performance (0.5–1 FPS).

## Requirements

- CrossOver
- [WineMetalGL 4.1.0](https://github.com/metalsharp/WineMetalGL/releases/latest)

## Installation

1. Install and enable WineMetalGL.
2. Enable **x87 Acceleration** in WineMetalGL Settings.
3. Download the shader fix from this repository.
4. Back up and replace `data/Shaders/v3f-t2f-c4f.frag` in the game's installation directory.
5. Launch the game through Steam.

## Recommended CrossOver settings

- Graphics backend: Wine
- Synchronization: MSync

## Tested on

- MacBook Air M3
- 8 GB RAM
- macOS 27.2.1
- WineMetalGL 4.1.0
- Another Brick in the Mall 1.2.3

The game runs smoothly in fullscreen mode with maximum graphics settings.

## Notes

- WineMetalGL Settings does not need to remain open while playing.
- Steam updates or file integrity verification may restore the original shader.
- This is an unofficial, community-made fix.
- Developed through AI-assisted debugging and verified through hands-on testing.
