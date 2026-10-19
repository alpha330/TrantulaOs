# Architecture baseline

Status: proposed direction; implementation and detailed design are pending.

## Execution model
The CPU runs the kernel and manages processes, memory, devices, and work submission. Suitable parallel jobs may execute on a GPU through a future compute service. A CPU implementation provides an initial correctness reference and execution alternative where supported.

Automatic offload of arbitrary Rust programs is outside the initial scope. Initial jobs must expose explicit input/output buffers and supported compute kernels.

## Memory model
RAM and VRAM are separate resource domains for initial design purposes. No transparent shared-memory behavior is assumed.
A device buffer must record its owner, size, access rights, lifetime, current execution state, and completion dependency. A buffer in use by a device must not be reused or freed until completion or confirmed device quiescence.
CPU page protections alone do not establish GPU isolation; DMA protection and GPU address-space enforcement require a separate design before untrusted GPU jobs are permitted.

## Fault handling
Distinguish submission, execution, synchronization, and result-validation errors. Mark incomplete output invalid. Use bounded waits where hardware permits. Device reset and recovery are hardware-dependent and are not guaranteed. Retry only jobs explicitly declared safe to replay.

## Two development tracks
1. Standalone Rust kernel: initial candidate target x86_64 in QEMU; bootloader and toolchain to be selected.
2. Hosted Rust compute experiment on Linux: validate CPU/GPU correctness and end-to-end performance using the actual RX 460.

Hosted graphics/compute libraries do not automatically provide a standalone OS driver. Display output and GPU compute are separate milestones.

## Open decisions
- Development host OS and reproducible toolchain.
- Bootloader, kernel organization, and initial device interfaces.
- RX 460 device identity, firmware requirements, usable compute API, and driver licensing.
- Project license.
- First benchmark workload and numerical precision requirements.
