# TrOs contributor instructions

## Scope
Build TrantulaOs (TrOs), an experimental Rust operating system. Prioritize computational correctness, isolation, and measured performance.

## Working rules
- Read README.md and docs/ before making architectural changes.
- Keep changes focused and use descriptive commits.
- Do not claim boot, hardware support, speedups, or test success without evidence.
- Prefer safe Rust. Every unsafe block must explain its safety invariants.
- Keep hardware-specific code behind narrow interfaces.
- Track CPU/GPU buffer ownership, lifetime, synchronization, and failure state explicitly.
- Do not silently retry non-idempotent GPU work or accept partial output as successful.
- Test CPU reference results against GPU output using workload-specific tolerances.
- Include data transfer and synchronization costs in performance reports.
- Keep hosted Linux experiments distinct from the standalone kernel.
- Do not add paid CI dependencies or require GPU hardware in ordinary CI.
- Until a runnable implementation exists, report validation as documentation-only.
- License selection belongs to the project owner; do not invent a license decision.
