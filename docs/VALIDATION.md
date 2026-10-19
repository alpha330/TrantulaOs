# Correctness and performance

## Correctness
- Use deterministic inputs and a CPU reference for each supported compute workload.
- Compare integer results exactly when arithmetic semantics match.
- Define absolute/relative tolerances and NaN/infinity behavior for floating-point workloads.
- Test empty inputs, non-aligned sizes, maximum supported sizes, invalid handles, and allocation failures.
- Exercise synchronization, cancellation, stale handles, and device failure where the backend supports them.
- Rust memory safety does not prove algorithm correctness or device isolation.

## Performance
Record hardware, OS, drivers, toolchain, workload size, precision, and build mode.
Separate cold initialization from warmed execution. Measure total latency including allocation, transfer, dispatch, synchronization, and readback; also report component timings when available.
Use repeated measurements and report distributions rather than a single best run.
Keep benchmark memory budgets explicit for the initial 8 GB RAM / 4 GB VRAM machine.
CPU/GPU duplicate execution is a validation mode, not the default production policy.

## Current evidence
Documentation baseline only. No build, boot, hardware compatibility, correctness, or performance results have been produced.
