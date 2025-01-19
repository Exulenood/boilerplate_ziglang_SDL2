# Zig SDL2 Boilerplate

A starting point for Zig projects with SDL2 integration and cross-compilation support for MacOS and Windows.

## Prerequisites

### MacOS

- Zig: `brew install zig` (tested with version 0.13.0)
  - Alternative download: [ziglang.org/download](https://ziglang.org/download/)
- SDL2: `brew install sdl2`
  - Alternative download: [SDL Releases](https://github.com/libsdl-org/SDL/releases/tag/release-2.30.11)
    Please note that you have to adjust the paths in the build.zig if you are not install SDL2 via Homebrew!

### Windows

- Zig (tested with version 0.13.0)
  - Download from [ziglang.org/download](https://ziglang.org/download/)
- SDL2: Download from [SDL Releases](https://github.com/libsdl-org/SDL/releases/tag/release-2.30.11)
  - Environment variable SDL2_PATH must be set to your SDL2 installation directory

## Build & Run

### MacOS

`zig build run`

### Windows

`zig build -Dtarget=x86_64-windows run`

## Project Structure

- `src/main.zig`: Main file with SDL2 initialization
- `build.zig`: Build script with cross-compilation support

## Troubleshooting

### Cross-compilation issues on MacOS

If you're building for Windows on MacOS and encounter SDL2 path issues:

1. The Homebrew SDL2 path might override your Windows SDL2 path
2. Try using the following command to isolate the environment:

```
env -i PATH="<path-to-your-zig-installation>"
SDL2_PATH="$SDL2_PATH"
zsh -c 'zig build -Dtarget=x86_64-windows'
```

3. If this works, check your environment variables for conflicting SDL2 paths

### Common Build Errors

- "SDL2_PATH is missing in env": Make sure you've set the SDL2_PATH environment variable on Windows
- "Unable to find SDL2 installation": On MacOS, verify your Homebrew installation or check custom SDL2 paths in build.zig
