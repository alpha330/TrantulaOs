# TrantulaOs (TrOs)

An experimental operating system project in Rust, exploring heterogeneous CPU/GPU computing with performance and computational correctness as primary goals.

**Status:** planning and architecture baseline. No bootable kernel, GPU driver, or benchmark implementation exists yet.

## Design direction
- CPU: kernel execution, resource management, interrupts, I/O, and sequential workloads.
- RAM: general system and application memory.
- GPU: explicitly supported parallel compute workloads.
- VRAM: device buffers with tracked ownership and synchronization.
- Select execution placement using measured end-to-end cost, including data transfers.
- Prefer safe Rust; isolate and document every unsafe boundary.

GPU acceleration is a research objective, not a promise that arbitrary applications or the kernel will execute faster on a GPU.

## Initial development hardware
User-reported: Intel Core i9-11900K, 8 GB RAM, AMD Radeon RX 460 with 4 GB VRAM. Exact GPU identity, driver/API compatibility, and host OS remain to be verified.

## Project documents
- [Architecture](docs/ARCHITECTURE.md)
- [Roadmap](docs/ROADMAP.md)
- [Correctness and performance](docs/VALIDATION.md)
- [Contributor instructions](AGENTS.md)

## Licensing
A project license has not been selected yet. Public visibility alone does not grant an open-source license. Choose and commit a license before accepting external contributions or describing the code as licensed open source.
