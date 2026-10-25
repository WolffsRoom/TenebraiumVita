# Development status — Tenebrarium for PS Vita

**Public status: no public build yet.**

These are development tests, not guarantees about a release build.

| Area | Status | Notes |
| --- | --- | --- |
| Boot | Working on physical Vita | Animated 960×544 splash, then native GXM |
| Title screen | Fix under test | Tiled panel backgrounds were stretched on the first build |
| Gameplay | Running on physical Vita | Testing in progress |
| Controls | Reworked, under test | Stick and touch move the pointer; D-pad moves between buttons only |
| Magnifier | Fix under test | Rendered through a real offscreen GXM target with a circular mask |
| Identifier | Under test | Works in host tests; needs device confirmation |
| Graphics | Native GXM 2D | Nine-patch (stretch, tile, tile-fit), polygons, lines; no custom shaders |
| Audio | Working | Music now loads on a background thread |
| Save/settings | Implemented by the game | Regression testing ongoing |
| Public downloadable build | Not available | No game files are distributed |

## Performance

The first device build ran below 60 FPS. The renderer now batches consecutive quads that share a texture into one GXM draw call and skips redundant clip changes; frame time, draw calls and GPU wait are logged every 300 frames for the next measurement. Sustained 60 FPS has **not** been confirmed.

## Loading

On the first build most of the boot time went to compiling the game's GDScript (~22 s) and loading the soundtrack (~6 s). Game data is now a single pack inside `game_data`, scripts ship pre-tokenized, and the soundtrack loads in parallel with script compilation.

## Known issues

- Shader effects (CRT, palette swaps, custom palette picker) are approximated or absent.
- Store links in the menu do not open anything on the Vita.
- Performance and loading improvements still need confirmation on hardware.

## Public files policy

This repository contains documentation only. No VPK, compiled port, game files or imported game caches are provided.

## References

- [Tenebrarium on itch.io](https://whatd0g.itch.io/tenebrarium)
- [Godot 4 Vita](https://github.com/WolffsRoom/godot4-vita)
- [README](../README.md)
