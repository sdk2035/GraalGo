# Validation and evidence

Status as of 2026-10-12: **not run**. No Go compiler or GraalVM LLVM runtime was available in the authoring environment. Documentation is not execution evidence.

## Planned fixture matrix

| Case | Expected result | Purpose |
| --- | --- | --- |
| add(20, 22) | 42 | Integer arithmetic |
| add(-7, 3) | -4 | Signed values |
| choose(0) | 0 | Zero branch |
| choose(1) | 1 | Positive branch |
| choose(-1) | -1 | Negative branch |
| Missing external symbol | Failure with retained diagnostic | Link/runtime boundary |
| Incompatible LLVM artifact | Failure with retained diagnostic | Toolchain mismatch |

Avoid integer overflow in the first fixtures; specify overflow semantics before adding boundary cases.

## Execution procedure

1. Record compiler/LLVM/GraalVM versions, platform and installation sources.
2. Build and execute a native reference.
3. Produce LLVM bitcode with the chosen frontend; inspect symbols and target metadata.
4. Resolve runtime dependencies and entry-point ABI explicitly.
5. Execute under Sulong with a timeout; capture output, return value and stderr.
6. Compare against the native reference and publish all commands and logs.

## Evidence template

- Commit and fixture identifier:
- OS and architecture:
- Compiler / LLVM / GraalVM distribution and versions:
- Build and execution commands:
- Artifact SHA-256:
- Native result:
- Sulong result:
- Required native libraries and unresolved symbols:
- Supported subset / limitations:
- Outcome: pass / fail / blocked, with diagnostic:

No compatibility or performance claim is accepted without this report.
