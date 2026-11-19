# Rig

A modular, terminal-based music production platform. Standalone apps share
`rig-core` (audio, MIDI, tempo, config) and `rig-components` (reusable UI)
via git submodules, and compose through system buses (PipeWire for audio,
MIDI for control). No tiling window manager; apps run independently and
route through the OS.

## Projects

| Directory | Purpose |
|---|---|
| `rig-core/` | Shared infrastructure: audio (miniaudio), MIDI, tempo, TOML config. |
| `rig-components/` | Reusable terminal UI components (audio panel, meter, lists, lamps). |
| `rig-looper/` | The looper app (Bubble Tea TUI + headless modes). |
| `rig-meter/` | Standalone capture-level meter. |
| `rig-template/` | Template for scaffolding new apps. |

The top-level directory is a **meta repository** for planning and notes only.
The subproject directories above are independent git repositories and are
gitignored here.

## Getting started

Prerequisites: Go 1.24+, CGO toolchain, and (for container audio) PipeWire +
WirePlumber.

```bash
# Build an app
cd rig-looper && make build      # produces ./rig-looper
cd rig-meter  && make build      # produces ./rig-meter

# Run the looper
./rig-looper                     # TUI (rtmidi engine)
./rig-looper -engine test -demo   # fake ports + synthetic events
./rig-looper -audio 5s           # headless audio check
./rig-looper -loop 2s            # headless looper round-trip
```

See `AGENTS.md` for build/packaging details, container audio internals, and
TUI gotchas.

## Architecture highlights

- **Audio**: miniaudio via `malgo` (CGO). Duplex stream keeps capture and
  playback sample-aligned for overdubs.
- **MIDI**: RtMidi via `gomidi`, plus a `test` engine for hardware-free runs.
- **Tempo**: internal `rig-core/tempo`; Ableton Link sync is optional/future.
- **Config**: TOML (`rig-core/config`).
- **Named ports**: apps report as `rig-looper:in` / `rig-looper:out` to
  PipeWire/PulseAudio.

## Roadmap

1. MIDI monitor — done
2. Audio I/O (enumeration, meter, round trip) — done
3. Single-channel looper — done (core); tempo-synced edges deferred
4. MIDI pedal mapping (config-driven)
5. Waveform display + position cursor
6. Multichannel / loop-in-loop
7. Ableton Link clock sync
8. Release packaging (prebuilt binaries)

## Project management

Tasks are tracked with [Backlog.md](https://github.com/MrLesk/Backlog.md) in
`backlog/` (Markdown + YAML frontmatter). Quick commands:

```bash
backlog task list
backlog board          # terminal Kanban
backlog browser        # web UI (port 6420)
```

See `AGENTS.md` for statuses, priorities, types, and conventions.

## License

TBD.
