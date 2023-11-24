This is a copy of [BB8 PostgreSQL transaction example][1]. [Cargo.toml](Cargo.toml) is copied from [here][2].
Building fails on Mac M2:

```
$ cargo build
    Updating crates.io index
   Compiling libc v0.2.150
   Compiling typenum v1.17.0
   Compiling lock_api v0.4.11
   Compiling quote v1.0.33
   Compiling tinyvec v1.6.0
   Compiling futures-channel v0.3.29
   Compiling ppv-lite86 v0.2.17
   Compiling futures-task v0.3.29
   Compiling syn v2.0.39
error: failed to run custom build command for `libc v0.2.150`

Caused by:
  process didn't exit successfully: `.../rust_libc_build_failure/target/debug/build/libc-4f9e2b02a856699f/build-script-build` (exit status: 101)
  --- stdout
  cargo:rerun-if-changed=build.rs

  --- stderr
  thread 'main' panicked at .../.cargo/registry/src/index.crates.io-6f17d22bba15001f/libc-0.2.150/build.rs:204:9:
  failed to run rustc: 
  note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
warning: build failed, waiting for other jobs to finish...
error: failed to run custom build command for `lock_api v0.4.11`

Caused by:
  process didn't exit successfully: `.../rust_libc_build_failure/target/debug/build/lock_api-cd5415232999f2f9/build-script-build` (exit status: 101)
  --- stderr
  thread 'main' panicked at .../.cargo/registry/src/index.crates.io-6f17d22bba15001f/autocfg-1.1.0/src/lib.rs:128:20:
  called `Result::unwrap()` on an `Err` value: Error { kind: Other("could not execute rustc") }
  note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace

```

How to fix it?

[1]: https://github.com/djc/bb8/blob/main/postgres/examples/txn.rs
[2]: https://github.com/djc/bb8/blob/main/postgres/Cargo.toml
