# GraalGo: architecture and requirements

## Boundary

The standard Go compiler is not the proposed LLVM-bitcode producer. Evaluate TinyGo as a candidate, with a deliberately bounded subset. Runtime initialization, garbage collection, scheduler, goroutines, channels, cgo, system calls and standard-library dependencies require individual compatibility evidence. Emitting bitcode does not establish Sulong compatibility.

## Components

1. Source fixtures with declared supported features.
2. Compiler adapter producing LLVM IR/bitcode and version metadata.
3. Artifact inspection: target triple, data layout, external symbols and required runtime libraries.
4. Sulong execution adapter using the selected GraalVM LLVM distribution.
5. Differential validation against the native reference.
6. Evidence report and optional future Java Polyglot host integration.

## Requirements

| ID | Requirement | Acceptance evidence |
| --- | --- | --- |
| R-01 | Pin the complete toolchain and platform | Versions and installation provenance |
| R-02 | Produce a bitcode fixture | Build command, artifact hash and LLVM inspection |
| R-03 | Resolve the entry point and dependencies | Exported symbols, ABI and dependency inventory |
| R-04 | Match native behavior for supported fixtures | Values, output and exit/error behavior |
| R-05 | Report incompatible inputs explicitly | Reproducible negative cases and diagnostics |
| R-06 | Bound execution | Documented timeout and process isolation for untrusted inputs |

## Out of initial scope

Full language compatibility, arbitrary packages, production deployment and performance claims. Garbage collection, exception/panic behavior, concurrency and host interop need separate specifications and acceptance gates.

## Milestones

- M0: architecture and validation plan (this repository).
- M1: toolchain feasibility report, including failures.
- M2: reproducible bounded Sulong pilot.
- M3: Java host contract and expanded differential fixtures.

Progress advances through evidence rather than an assumed percentage.
