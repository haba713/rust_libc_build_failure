Building the crate [libc](https://crates.io/crates/libc) fails on Mac with
Apple silicon architecture. I've tested with
`cargo build --target aarch64-apple-darwin` and 
`cargo build --target x86_64-apple-darwin`.

How to fix it?

```
% cargo build
   Compiling libc v0.2.150
error: failed to run custom build command for `libc v0.2.150`

Caused by:
  process didn't exit successfully: `/Users/Shared/rust_libc_build_failure/target/debug/build/libc-4f9e2b02a856699f/build-script-build` (exit status: 101)
  --- stdout
  cargo:rerun-if-changed=build.rs

  --- stderr
  thread 'main' panicked at /Users/u2/.cargo/registry/src/index.crates.io-6f17d22bba15001f/libc-0.2.150/build.rs:204:9:
  failed to run rustc: 
  note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace`
```

See the details [here](build_error.txt).

The environment:
- macOS 13.6.1, Apple Silicon M2
- cargo 1.74.0 (ecb9851af 2023-10-18)
- rustc 1.74.0 (79e9716c9 2023-11-13)