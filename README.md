## Assets used
[Thank you kind sir for the Toyota model](https://skfb.ly/p9u7r)

## About the fork
Fork [orhun/ratty](https://github.com/orhun/ratty) into `this repo` - a cursor-focused terminal emulator with morph-mod squish/stretch animation and all upstream features intact.

## Current State (morph-only branch)
Clean fork from upstream with only morph-mod changes applied on top:

### Features (all upstream preserved)
- Terminal rendering (GPU-accelerated via Bevy)
- Kitty graphics protocol
- Kitty keyboard protocol
- RGP (remote graphics protocol)
- Inline objects
- Mobius strip 3D mode
- Terminal plane warp
- 3D mode toggle
- Clipboard (copy/paste)
- Font controls
- Theme/palette support

### Morph-mod additions
- **`config.rs`**: `morph_enabled`, `morph_amplitude` in `CursorAnimationConfig`; `y_offset`, `scale3`, `rotation` in `CursorModelConfig`
- **`systems.rs`**: `cursor_pose` returns `Vec3` scale with morph formula (squish/stretch synced to bob); `sync_rgp_objects` applies same morph to animated inline objects
- **`cli.rs`**: updated about text

## Build
- **Debug**: `cargo check` - passes
- **Release**: `cargo build --release`

## Config
Binary reads `~/.config/ratty/ratty.toml`. Example config:

```toml
[cursor.model]
path = "/home/chair/.config/ratty/models/bouncy_toyota_yaris.glb"
scale_factor = 0.5
brightness = 0.5
x_offset = 2
y_offset = 0.0
plane_offset = 18.0
visible = true
scale3 = [1.0, 1.0, 1.0]
rotation = [0.0, 0.45, 0.0]

[cursor.animation]
spin_speed = 0.00
bob_speed = 7
bob_amplitude = 0.2
morph_enabled = true
morph_amplitude = 0.2
