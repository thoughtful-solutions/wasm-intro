# A Brief introduction to WASM

WebAssembly (WASM) is a binary instruction format for stack-based virtual machines, 
designed as a low-level compilation target for high-level languages.

Key aspects:
- Binary format for executable code in web browsers
- Near-native performance
- Secure, sandboxed execution environment
- Language-agnostic (C++, Rust, Go, etc. can compile to WASM)
- Two formats: 
  - Text (.wat) for human-readable assembly
  - Binary (.wasm) for execution

Use cases:
- Browser-based applications requiring high performance
- Server-side applications (via WASI)
- Cross-platform development
- Gaming and multimedia processing
- Extending web applications with native code

The use case may require specific runtimes such as
- Browser Engines
Function: Execute WASM in browser environment, integrate with JS
  * V8 (Chrome/Node.js)
  * *SpiderMonkey (Firefox)
  * JavaScriptCore (Safari)
 
-Standalone Runtimes
Function: Execute WASM outside browser, system integration
  * Wasmtime: Reference implementation of WASI
  * Wasmer: Supports multiple backends, embedable
  * WAMR (WebAssembly Micro Runtime): IoT/embedded focus
  * WasmEdge: Cloud native, Kubernetes integration

-Language-specific
  Function: Optimize for specific language environments
  * Lucet (Rust): AOT compilation
  * GraalWasm (Java): JVM integration


# Comparision wiht other Web Technologies

JavaScript:
* Interpreted scripting language
* Runs in browsers and Node.js
* Dynamic typing
* Single-threaded with event loop
* Primary for web development

Java:
* Compiled to bytecode for JVM
* Platform independent ("Write once, run anywhere")
* Static typing
* Multi-threaded
* Enterprise/desktop/mobile applications

WASM:
* Binary instruction format
* Compilation target for other languages
* Near-native performance
* Runs in browser or standalone
* Low-level, language-agnostic
* No garbage collection (unless provided by source language)

Key Difference: 
* JavaScript and Java are programming languages, 
  while WASM is a compilation target/binary format.
* JavaScript JIT must handle dynamic typing and frequent changes,
while Java JIT makes aggressive optimizations based on static type guarantees.
* WASM prioritizes portability and security through abstraction,
   while native formats, such as ELF, optimize for direct hardware/OS integration

   