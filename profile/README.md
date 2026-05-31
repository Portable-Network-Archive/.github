# Portable Network Archive

**Portable Network Archive (PNA)** is an open archive format and Rust-based toolchain for portable, streamable, compressible, encryptable, and splittable archives.

PNA is inspired by PNG's chunk-oriented data structure. It is designed to work as a practical archive format for command-line tools, libraries, WebAssembly demos, GUI applications, and virtual filesystem integrations.

[Specification](https://portable-network-archive.github.io/Portable-Network-Archive-Specification/) | [CLI and library](https://github.com/ChanTsune/Portable-Network-Archive) | [Crates.io](https://crates.io/crates/portable-network-archive) | [Docs.rs](https://docs.rs/portable-network-archive) | [WebAssembly demo](https://portable-network-archive.github.io/wasm-demo/)

## Why PNA?

- **Portable archive structure**: PNA is built around a well-specified chunk layout, making the format easier to extend and implement.
- **Compression flexibility**: PNA supports zlib, zstd, and xz, including per-file and archive-wide workflows.
- **Strong encryption**: PNA supports 256-bit AES and 256-bit Camellia for protecting archive contents.
- **Splittable archives**: The format is designed so large archives can be divided into smaller parts.
- **Streamable processing**: Archives can be read and written serially, making PNA suitable for streaming and transport-oriented use cases.
- **Metadata-minimal by design**: A PNA archive can omit everything except the entry name and payload when timestamps, permissions, owner IDs, comments, or other metadata are not needed.
- **Attribute preservation when needed**: The CLI can preserve permissions, timestamps, extended attributes, and experimental ACL data.

## Get Started

Install the CLI from Crates.io:

```sh
cargo install portable-network-archive
```

Create, extract, and inspect a PNA archive:

```sh
pna create -f archive.pna file1.txt file2.txt
pna extract -f archive.pna
pna list -f archive.pna
```

Prefer a tar-like interface? The CLI also provides a bsdtar-compatible command surface:

```sh
pna compat bsdtar -cf archive.pna file1.txt file2.txt
pna compat bsdtar -xf archive.pna
pna compat bsdtar -tf archive.pna
```

## Projects

| Repository | What it provides |
| --- | --- |
| [ChanTsune/Portable-Network-Archive](https://github.com/ChanTsune/Portable-Network-Archive) | Main Rust workspace: CLI, `pna` crate, `libpna` encoding/decoding library, tests, and release tooling. |
| [Portable-Network-Archive-Specification](https://github.com/Portable-Network-Archive/Portable-Network-Archive-Specification) | The PNA file format specification, hosted on GitHub Pages. |
| [fs](https://github.com/Portable-Network-Archive/fs) | `pnafs`, a FUSE-based virtual filesystem for mounting PNA archives as disk-like filesystems. |
| [wasm-demo](https://github.com/Portable-Network-Archive/wasm-demo) | Browser demo for creating and extracting PNA archives with WebAssembly. |
| [pna-gui](https://github.com/Portable-Network-Archive/pna-gui) | Tauri, React, and TypeScript GUI for working with PNA archives. |

## For Implementers

The format specification covers the archive file structure, chunk ordering rules, compression algorithms, encryption modes, key derivation, data representation, and encoder/decoder recommendations.

Start with the hosted specification:

- [PNA Specification](https://portable-network-archive.github.io/Portable-Network-Archive-Specification/)
- [Main implementation repository](https://github.com/ChanTsune/Portable-Network-Archive)
- [`pna` crate documentation](https://docs.rs/pna)
- [`libpna` crate documentation](https://docs.rs/libpna)

## Contributing

Contributions, bug reports, interoperability feedback, and implementation experiments are welcome. For code changes, start with the repository that matches the area you want to work on. For format-level questions or proposals, use the specification repository.
