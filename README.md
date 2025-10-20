# INFO

Transpiler is written in JS. The goal is to provide a universal language that can fit different needs while remaining easy & flexible.
This means a variable can be auto interpreted and inferred for a script like setup or be given specific type info.
The performance goal is dependent upon the compile target and feature use such as memory safety or built in GC.
The language acts as syntactical sugar over compile target languages which expands its viability to all possible platforms.
This is most ideal for low level compile targets with an initial focus on transpiling to Zig.
While transpiling to a language like Javascript or Typescript can provide hot code reloading and quick testing.

Targeting different compile target's libraries can differ via the import syntax: node:crypto, zig:crypto and a universal wrapper such as crypto.

Eventually compiling by itself to a raw binary would be possible via LLVM etc.
This would avoid the use of compiling to other low-level languages and directly into actionable bytecode or machine code.
However, transpiling to other languages is the focus for now which results in speeds relative to those languages.

Low level transpile target languages

1) Zig (priotity)
2) Carbon
3) Rust
4) Go

High level transpile target languages

1) Javascript (priotity)
2) Typescript
3) Env (Bun, Nodejs, Deno)
