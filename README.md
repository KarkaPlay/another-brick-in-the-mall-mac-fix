# How to play Another Brick in the Mall on Mac

A simple guide to running **Another Brick in the Mall** on Apple Silicon Macs using CrossOver and WineMetalGL.

This guide fixes two major compatibility issues:

- Extremely low in-game performance (0.5–1 FPS).
- Startup crash when using WineMetalGL.

## Step 1 — Install the game

1. Install [CrossOver](https://www.codeweavers.com/crossover).
2. Install Steam in a CrossOver bottle.
3. Download Another Brick in the Mall through Steam.

## Step 2 — Install WineMetalGL

1. Download [WineMetalGL](https://github.com/metalsharp/WineMetalGL/releases/latest).
2. Open the WineMetalGL Settings application.
3. Install WineMetalGL into CrossOver and enable it.

## Step 3 — Fix low FPS

Open WineMetalGL Settings and enable **x87 Acceleration**.

This is the most important setting for performance. Without it, the game may run at approximately 0.5–1 FPS, even on an empty map.

## Step 4 — Fix the startup crash

WineMetalGL 4.1.0 has a GLSL compatibility issue that causes the game to crash on startup.

1. Download the fixed [v3f-t2f-c4f.frag](./v3f-t2f-c4f.frag) shader from this repository.
2. Open Steam and right-click the game.
3. Select **Manage → Browse local files**.
4. Navigate to `data/Shaders/`.
5. Back up the original `v3f-t2f-c4f.frag` file.
6. Replace it with the downloaded file.

## Step 5 — Configure CrossOver

Use the following bottle settings:

| Setting | Value |
|---|---|
| Graphics backend | Wine |
| Synchronization | MSync |
| WineMetalGL | Enabled |
| x87 Acceleration | Enabled |

Restart the CrossOver bottle and launch the game through Steam.

You can now close WineMetalGL Settings — it does not need to remain open while playing.

## Results

The game runs smoothly in fullscreen mode with maximum graphics settings on the following hardware:

| Component | Specification |
|---|---|
| Mac | MacBook Air M3 |
| RAM | 8 GB |
| macOS | 27.2.1 |
| WineMetalGL | 4.1.0 |
| Game version | 1.2.3 |

## Technical explanation

Two separate compatibility issues were identified:

- **Low FPS:** The issue appears to be related to inefficient translation of legacy x87 floating-point instructions. Enabling x87 Acceleration resolves the observed performance problem.
- **Startup crash:** A naming collision between a sampler variable and the modern GLSL `texture()` function appears to cause a shader compilation error in WineMetalGL. Renaming the sampler variable resolves the crash.

## Troubleshooting

- Steam updates or file integrity verification may restore the original shader. Simply reapply the fix.
- Updating CrossOver may require reinstalling WineMetalGL.
- If you encounter additional issues, feel free to open an issue in this repository.

## Disclaimer

This is an unofficial, community-made compatibility fix. It was developed through AI-assisted debugging and verified through hands-on testing on Apple Silicon hardware.
