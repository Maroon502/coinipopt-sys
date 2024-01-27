# Coinpopt-sys

[![Package][package-img]][package-url] [![Documentation][documentation-img]][documentation-url] [![License][license-img]][license-url]

coinipopt-sys crate is a *-sys crate. The package provides Low-level bindings to the [Ipopt] library.

By this package, you don't need to worry about installing Ipopt in the system, and it's a package for **all platforms**.

Ipopt (Interior Point OPTimizer, pronounced eye-pea-Opt) is a software package for large-scale nonlinear optimization. It is designed to find (local) solutions of mathematical optimization problems of the NLP.

## Usage

Just add the following to your `Cargo.toml`:

```toml
[dependencies]
coinipopt-sys = "0.2"
```

## Configuration

The following Cargo features are supported:

* `default` to `osiclp` and `clpsolver` feature;
* `osiclp` to build with Osi supported;
* `clpsolver` to build `ClpSolver` lib and crate the api for `Rust`. If you do not use `Clp` directly, you can disable this feature to reduce the build time;

The package build from the source and link statically by default. It also provide the following environment variables to allow users to link to system library customly:

* `CARGO_IPOPT_STATIC` to link to Ipopt statically;
* `CARGO_IPOPT_SYSTEM` to link to Ipopt system library;

Set the environment variable to `1` to enable the feature. For example, to link to system library dynamically, set `CARGO_${LIB_NAME}_SYSTEM` to `1`; to link to system library statically, set both `CARGO_${LIB_NAME}_SYSTEM` and `CARGO_${LIB_NAME}_STATIC` to `1`.

You can also use `ipopt-sys` with `no-default-features`, and add `ipopt-src` to the `Cargo.toml` and enable the related feature defined by `ipopt-src`. Please see [Ipopt-src].

## Windows and vcpkg

On Windows, if `${LIB_NAME}_SYSTEM` is set to `1`, `ipopt-src` will use [vcpkg] to find Ipopt. Before building, you must have the correct Ipopt installed for your target triplet and kind of linking. For instance, to link dynamically for the `x86_64-pc-windows-msvc` toolchain, install  `ipopt` for the `x64-windows` triplet:

```sh
vcpkg install ipopt --triplet x64-windows
```

To link Ipopt statically, install `ipopt` for the `x64-windows-static-md` triplet:

```sh
vcpkg install ipopt --triplet x64-windows-static-md
```

To link Ipopt and C Runtime (CRT) statically, install `ipopt` for the `x64-windows-static` triplet:

```sh
vcpkg install ipopt --triplet x64-windows-static
```

and build with `+crt-static` option

```sh
RUSTFLAGS='-C target-feature=+crt-static' cargo build --target x86_64-pc-windows-msvc
```

Please see the ["Static and dynamic C runtimes" in The Rust reference](https://doc.rust-lang.org/reference/linkage.html#static-and-dynamic-c-runtimes) for detail.

## Cross Compilation

Because [openblas-src]'s Issue [#101](https://github.com/blas-lapack-rs/openblas-src/issues/101), we can't cross compile the package with `openblas-static` feature. So, if you want to cross compile the package, you could use [mike-kfed](https://github.com/mike-kfed/openblas-src/tree/arm-cross-compile) instead.

Add this to your `project/.cargo/config.toml`.

```toml
[patch.crates-io]
openblas-src = { git = "https://github.com/mike-kfed/openblas-src.git", branch = "arm-cross-compile" }
```

you can compile it for the other target by providing the `--target` option to `cargo build`.

| Target                               |  supported  |
|--------------------------------------|:-----------:|
| `arm-unknown-linux-gnueabi`          | ✓   |
| `arm-unknown-linux-gnueabihf`        | ✓   |
| `armv7-linux-androideabi`            | ✓   |
| `armv7-unknown-linux-gnueabi`        | ✓   |
| `armv7-unknown-linux-gnueabihf`      | ✓   |
| `armv7-unknown-linux-musleabi`       | ✓   |
| `armv7-unknown-linux-musleabihf`     | ✓   |
| `riscv64gc-unknown-linux-gnu`        | ✓   |
| `x86_64-pc-windows-msvc`              | ✓   |
| `x86_64-unknown-linux-gnu`           | ✓   |

## Contribution

Your contribution is highly appreciated. Do not hesitate to open an issue or a
pull request. Note that any contribution submitted for inclusion in the project
will be licensed according to the terms given in [LICENSE](license-url).

[Ipopt]: https://github.com/coin-or/Ipopt
[Ipopt-src]: https://github.com/Maroon502/ipopt-src

[documentation-img]: https://docs.rs/coinipopt-sys/badge.svg
[documentation-url]: https://docs.rs/coinipopt-sys
[package-img]: https://img.shields.io/crates/v/coinipopt-sys.svg
[package-url]: https://crates.io/crates/coinipopt-sys
[license-img]: https://img.shields.io/crates/l/coinipopt-sys.svg
[license-url]: https://github.com/Maroon502/coinipopt-sys/blob/master/LICENSE.md