# lerc-sys

[![Crates.io](https://img.shields.io/crates/v/lerc-sys)](https://crates.io/crates/lerc-sys)
[![Docs.rs](https://docs.rs/lerc-sys/badge.svg)](https://docs.rs/lerc-sys)

Low-level Rust FFI bindings to [Esri's LERC](https://github.com/Esri/lerc) compression library (C API).

This crate provides raw, unsafe bindings generated via `bindgen`, and builds the LERC C++ source using `cc`.

## Build

This crate **vendors** the LERC C++ sources and compiles them automatically using `cc`. It does not require a system-installed `libLerc`.

## WASM Support

For WASM targets (e.g. `wasm32-unknown-emscripten`), this crate uses pregenerated bindings since `bindgen` cannot parse headers for WASM. Native builds generate bindings dynamically via `bindgen`.

### Regenerating Bindings

If you update the vendored liblerc sources, regenerate the pregenerated bindings:

```bash
# Build for native target (generates fresh bindings via bindgen)
cargo build

# Copy generated bindings to source tree
cp target/debug/build/lerc-sys-*/out/bindings.rs src/bindings_pregenerated.rs
```

## Status

✅ Supports LERC 4.0+
✅ Linux tested
✅ Automatically generates bindings to `Lerc_c_api.h`

## License

Apache-2.0
