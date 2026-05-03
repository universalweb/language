# ⩝ Language

Human & Agentic Co-development First language

`⩝` is an experimental programming language designed for AI-and-human co-development. The goal is to make code more concise, expressive, and easier to co-author without giving up the ability to target practical runtimes and lower-level backends.

The language is aimed at three overlapping use cases:

- next-generation smart contracts, smart specs and other sandboxed environments
- high-level scripting and fast iteration
- performance-oriented applications that benefit from lower-level compilation targets

Its syntax direction borrows some of the feel of JavaScript, Carbon, and Zig, while trying to stay smaller, more flexible, and more token-efficient.

## What the language is trying to do

This project is built around a simple idea: one language should be able to scale from quick scripts to stricter, systems-style code.

That means the language is being designed to support:

- compact syntax with less boilerplate
- token-efficient code that is easier for AI and humans to write together
- inferred types when convenience matters
- explicit types when control and performance matter
- a smooth path from high-level development to lower-level targets

## Transpiler-first by design

This language is being designed as a **transpiler-first** language rather than a native-compiler-first one.

The initial implementation is intended to be written in JavaScript so the tooling stays modular, easy to extend, and approachable to experiment with. In the near term, the language acts as a high-level source language that can be lowered into other targets.

Longer term, direct compilation to bytecode or native binaries could be possible through LLVM-style backends or similar technology, but that is not the current priority.

## Core ideas being explored

The files in `design/` show the current language direction. Some of the main themes are:

- **AI-first ergonomics** — less repetition, fewer tokens, and clearer patterns for co-development
- **Flexible typing** — scripting-friendly inference with the option for explicit low-level type information
- **Async-friendly flow** — built-in ideas around `await`, `defer`, concurrency helpers, and multi-value returns
- **Target-aware imports** — imports such as `node:crypto`, `zig:crypto`, or a universal wrapper like `crypto`
- **Safer execution models** — permissions, restricted environments, memory-safety options, and fault isolation
- **High-level language features** — pipes, observables, template syntax, structured objects, and scope-based resource patterns

## Why transpile?

Transpilation keeps the language flexible.

It allows the same source language to target:

- fast feedback loops through JavaScript or TypeScript
- lower-level performance through systems-oriented targets such as Zig
- environment-specific libraries without changing the core language model

Performance and safety depend on the chosen backend and enabled features. A scripting target may emphasize iteration speed and hot reloading, while a systems target may emphasize stronger typing, memory control, or restricted execution.

## Planned targets

### Lower-level targets

1. Zig *(current priority)*
2. WebAssembly (WASM)
3. Carbon
4. Rust
5. Go

### Higher-level targets

1. JavaScript *(current priority)*
2. TypeScript
3. Runtime environments such as Bun, Node.js, and Deno

## Example direction

The syntax is still experimental, but the design direction looks something like this:

```lang
function example(arg = 'default') !void, !string {
	await fnThatCanBeAsyncByDefault();
	defer thisRunsAfterTheFunction();
	return arg;
}
```

This example highlights some of the ideas being explored: concise function syntax, async-friendly defaults, and multi-value return support.

## Current repository status

This repository is currently focused on **language design and syntax exploration**.

Most of the work today lives in:

- `design/` — language feature experiments and syntax sketches
- `ai/` — AI-oriented notes and supporting ideas

In other words, this repository describes the language direction and early prototype thinking. It is not a finished compiler yet.

## Naming

Working names under consideration include:

- `⩝`
- `⩝Lang`
- `V-`
- `V Dash`
- `VHD`

## Smart Specifications instead of Smart Contracts

Smart Specifications are a strict, data-first way to describe valid state changes. They can be rendered as JSON for interoperability, but they are intended to be encoded primarily as CBOR or other structured binary formats.

Instead of treating the contract itself as the only place where logic can live, this model treats the specification as the source of truth. The schema defines what is valid, while external runtimes—whether AI systems or standard software—deterministically compute the same state transition from the same input.

That approach is intended to provide several benefits:

- a stricter and more portable contract surface
- deterministic state generation without requiring the language to be compiled on-chain
- logic that can live outside the blockchain, script, or network layer
- runtimes that can receive long-term security updates without changing the specification format
- compatibility with both AI-driven execution and conventional software execution

The goal is a smart-contract-like model with stronger structure, easier upgrades, and potentially cheaper consensus based on verified state transition outputs.