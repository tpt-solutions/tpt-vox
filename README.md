# tpt-vox

A unified, Rust-native, high-performance audio inference engine: real-time streaming (robotics, voice agents) and high-fidelity batch media generation (audiobooks, dubbing). `no_std`-compatible core, zero-copy buffers, offline-first.

See [spec.txt](spec.txt) for the design and [TODO.md](TODO.md) for progress.

## Crates (planned)

| Crate | Role |
|---|---|
| `tpt-vox-core` | `no_std` primitives: `AudioBuffer`, `AudioStream`, traits, `VoxError` |
| `tpt-vox-stream` | Real-time engine: VAD, barge-in, chunked STT/TTS |
| `tpt-vox-studio` | Batch media engine: high-fidelity TTS, timestamps |
| `tpt-vox-gpu` | `tpt-gpu` backend |
| `tpt-vox-crucible` | `tpt-crucible` edge NPU/FPGA backend |
| `tpt-vox-mesh` | `tpt-tessera` decentralized compute |

## License

Licensed under either of

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE))
- MIT license ([LICENSE-MIT](LICENSE-MIT))

at your option.

Copyright (c) 2026 TPT Solutions.
