# Coinpopt-sys

[![Package][package-img]][package-url] [![Documentation][documentation-img]][documentation-url] [![License][license-img]][license-url]

`coinipopt-sys` crate is a *-sys crate. The package provides Low-level bindings to the [Ipopt] library.

By this package, you don't need to worry about installing Ipopt in the system, and it's a package for **all platforms**.

Ipopt (Interior Point OPTimizer, pronounced eye-pea-Opt) is a software package for large-scale nonlinear optimization. It is designed to find (local) solutions of mathematical optimization problems of the NLP.

## Usage

Just add the following to your `Cargo.toml`:

```toml
[dependencies]
coinipopt-sys = "\*"
```

## Configuration

You can use `ipopt-sys` with `no-default-features`, and add `ipopt-src` to the `Cargo.toml` and enable the related feature defined by `ipopt-src`. Please see [Ipopt-src].

## Library Linking and Cross Compile

if you want to know the detail about how it compile or link the Ipopt, please see [Ipopt-src].

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