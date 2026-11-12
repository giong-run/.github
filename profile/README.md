<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="giong-logo-dark.svg">
    <img alt="giong" src="giong-logo-light.svg" width="300">
  </picture>
</p>

<p align="center"><b>A thread-per-core async runtime for Rust on Linux, built directly on io_uring.</b></p>

<p align="center">
  <a href="https://giong.run">giong.run</a> ·
  <a href="https://github.com/giong-run/Giong">Repository</a> ·
  <a href="https://docs.rs/giong">Docs</a>
</p>

Named after Thánh Gióng, the child of Vietnamese legend who lay silent for three years and
then rose a giant: giong costs next to nothing while idle and uses every core the moment
load arrives.

- **One system call per tick, not per operation.** A whole turn of the event loop goes to
  the kernel in a single `io_uring_enter`.
- **A latency dial.** `spin_before_park` trades a little idle CPU for lower latency on
  quiet connections.
- **Cancellation-safe by construction.** Dropping an I/O future never frees memory the
  kernel may still write to.
- **Small enough to read.** A few thousand lines, few dependencies, and a comment on every
  `unsafe` block.

giong needs Linux 6.0 or newer. Benchmarks, with the method and the cases where it does
not win, are in the [repository README](https://github.com/giong-run/Giong#benchmarks).

Licensed under MIT OR Apache-2.0. Issues and pull requests are welcome.
