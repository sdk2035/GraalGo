# GraalGo

Experimental Go / LLVM / GraalVM research laboratory maintained under sdk2035.

**One project per language:** TruffleGo is a conceptual alias within this repository, not a second repository or an implemented AST interpreter. These are portfolio project names, not official GraalVM language distributions.

## Technical status

Architecture and research plan, created 2026-10-12. No validated Sulong execution or production-ready Go runtime is delivered. “Experimental / research” describes the intended workstream; it is not evidence of a published academic implementation.

## Proposed mechanism

`Go source → candidate LLVM frontend (TinyGo) → LLVM bitcode → Sulong (Truffle) → GraalVM`

The standard Go compiler is not the proposed LLVM-bitcode producer. Evaluate TinyGo as a candidate, with a deliberately bounded subset. Runtime initialization, garbage collection, scheduler, goroutines, channels, cgo, system calls and standard-library dependencies require individual compatibility evidence. Emitting bitcode does not establish Sulong compatibility.

Sulong supplies the Truffle-based LLVM execution layer. A direct Go AST interpreter would be a separate future design decision within this same project.

## Initial scope

- Deterministic integer arithmetic and conditional control flow.
- Native reference results compared with execution of the same workload through Sulong.
- Recorded compiler, LLVM and GraalVM versions, OS, architecture, commands and logs.
- Explicit rejection or documentation of unsupported language/runtime features.

See [architecture and requirements](docs/specification.md) and [validation plan](docs/validation.md).

## Next task

**GGO-001:** select and pin a compatible toolchain; produce one minimal bitcode artifact; capture native and Sulong results or a reproducible incompatibility report. Do not label the project a working pilot until the end-to-end evidence is committed.

## References

- [GraalVM LLVM compilation](https://www.graalvm.org/latest/reference-manual/llvm/Compiling/)
- [Sulong upstream](https://github.com/oracle/graal/tree/master/sulong)
- [TinyGo compiler pipeline](https://tinygo.org/docs/concepts/compiler-internals/pipeline/)
- [TinyGo compatibility](https://tinygo.org/docs/reference/lang-support/)

## Portfolio

[Profile](https://github.com/sdk2035) · [Companion project](https://github.com/sdk2035/GraalRust)
