# Roadmap

All implementation milestones are pending.

## M0 — Baseline and environment
- [x] Record project goals, hardware, and architectural boundaries.
- [ ] Select project license.
- [ ] Confirm development host OS and GPU device identity.
- [ ] Verify GPU compute API/driver compatibility using primary documentation and an actual device test.
- [ ] Select and pin Rust toolchain, bootloader, and QEMU configuration.

Exit: documented reproducible setup and explicit unsupported capabilities.

## M1 — First boot
Build a minimal standalone Rust kernel with serial logging, panic reporting, and a repeatable QEMU boot smoke test. No disk writes to physical hardware.
Exit: reproducible build and captured successful boot output.

## M2 — Kernel foundations
Implement physical/virtual memory management, exception/interrupt handling, timer support, and basic task execution incrementally.
Exit: tests for allocation boundaries, exception behavior, and scheduling progress.

## M3 — Hosted CPU/GPU experiment
Implement a deterministic CPU reference and one explicitly supported GPU workload.
Exit: validated results, boundary-case tests, and end-to-end timing across multiple input sizes. Report cases where CPU wins.

## M4 — Isolation
Introduce userspace boundaries and define device/DMA isolation before admitting untrusted GPU workloads.
Exit: negative tests demonstrate that forbidden memory access is rejected.

## M5 — Standalone GPU feasibility
Investigate one specific GPU and documented submission/memory interfaces. Start with device discovery; keep display and compute separate.
Exit: hardware feasibility report, then a bounded trusted compute demonstration if feasible.

## M6 — Execution placement
Use measured job characteristics to select CPU or GPU for supported workloads.
Exit: repeatable performance evidence with correctness checks and explicit recovery limits.
