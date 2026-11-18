# tpt-vox TODO

Legend: `[ ]` todo, `[x]` done. Spec: [spec.txt](spec.txt).

## 0. Repo setup
- [x] Dual license files (MIT OR Apache-2.0, TPT Solutions)
- [x] README.md
- [x] Root `Cargo.toml` workspace
- [x] `.gitignore`
- [x] Verify tpt-crucible git URL resolves (tpt-solutions/tpt-crucible: OK)
- [ ] `git init`, add remote `https://github.com/tpt-solutions/tpt-vox`, first commit
- [ ] Verify git URLs for tpt-archon, tpt-gpu, tpt-telos (tpt-solutions) and tpt-tessera (tpt-labs)
- [ ] CI: fmt, clippy, test, `no_std` build check (`thumbv7em-none-eabihf`)
- [ ] `deny.toml` (cargo-deny: licenses, advisories)
- [ ] CONTRIBUTING / CHANGELOG (when needed)
- [ ] Decide feature-flag scheme for optional tpt deps (`archon`, `gpu`, `crucible`, `tessera`, `telos`)

## Phase 1: Foundation & Core Primitives (weeks 1-3)
- [ ] Create workspace crates: core, stream, studio, gpu, crucible, mesh
- [ ] `tpt-vox-core` as `#![no_std]` (alloc optional)
- [ ] `VoxError` (no_std error enum)
- [ ] `AudioBuffer<'a>`: PCM/Float32 data, sample rate, channels
- [ ] `AudioStream`: async iterator yielding chunks
- [ ] Trait `StreamingTranscriber`
- [ ] Trait `BatchTranscriber`
- [ ] Trait `ChunkSynthesizer`
- [ ] Trait `BatchSynthesizer`
- [ ] tpt-archon zero-copy page mapping for `AudioBuffer` (feature-gated)
- [ ] Unit tests + doc tests; verify core builds on a bare-metal target
- [ ] API docs

## Phase 2: Streaming Engine & Edge (weeks 4-7)
- [ ] `tpt-vox-stream` crate skeleton
- [ ] VAD: no-alloc, bounded loops, panic-free (designed for tpt-telos proof)
- [ ] VAD latency benchmark (<10 ms)
- [ ] Barge-in: abort TTS stream on detected user speech
- [ ] Chunked STT pipeline (100-500 ms frames, partial transcripts)
- [ ] Port Whisper-Tiny wrapper from `../models/whisper-tiny.en-tpt`
- [ ] WER validation using `../models/wer` + `testaudio`
- [ ] `tpt-vox-crucible`: ONNX/Safetensors -> edge compile path (ARM NPU target)
- [ ] End-to-end streaming latency benchmark (<200 ms)
- [ ] tpt-gpu fallback path for streaming

## Phase 3: Studio Engine & GPU (weeks 8-12)
- [ ] `tpt-vox-studio` crate skeleton
- [ ] `tpt-vox-gpu` backend on tpt-gpu (deterministic VRAM)
- [ ] Mel-spectrogram kernel (CUDA/HIP)
- [ ] Audio cross-attention kernel
- [ ] DMA zero-copy path from archon buffers to GPU
- [ ] Kokoro-82M wrapper (fast TTS)
- [ ] F5-TTS wrapper (media TTS, zero-shot cloning)
- [ ] Long-document text chunking + parallel batch scheduling
- [ ] Word-level timestamps
- [ ] Phoneme-level timestamps
- [ ] JSON manifest output
- [ ] WAV writer
- [ ] Audiobook demo (50,000-word input)
- [ ] Deterministic VRAM allocation tests

## Phase 4: Mesh Integration & Verification (weeks 13-16)
- [ ] `tpt-vox-mesh` skeleton on tpt-tessera
- [ ] Peer discovery
- [ ] Secure (encrypted) audio relay over Wi-Fi/BLE
- [ ] Dynamic quorum consensus for transcripts
- [ ] Byzantine peer failure tests
- [ ] Local-vs-mesh routing policy (offload when NPU exhausted)
- [ ] tpt-telos proofs: VAD
- [ ] tpt-telos proofs: mesh routing consensus
- [ ] Proof that "stop" command can't be dropped (no buffer overflow / race)
- [ ] Privacy/compliance doc (offline-first, no cloud callbacks; NZISM, HIPC 2020, HIPAA notes)
- [ ] Release v1.0 (changelog, crate metadata, tag)

## Later / optional models
- [ ] SenseVoice-Small / Large
- [ ] Whisper-Large-v3-Turbo (studio STT)
- [ ] Piper (streaming TTS)
- [ ] Chatterbox (emotional TTS)
