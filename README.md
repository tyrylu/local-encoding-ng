local-encoding-ng
====

[![Crates.io](https://img.shields.io/crates/v/local-encoding-ng.svg)](https://crates.io/crates/local-encoding-ng)

This is local-encoding-ng, a library which wastly simplifies dealing with the unfamous Windows 8-bit encodings.

For example, in Russian version:

 * [`CP-1251`](https://en.wikipedia.org/wiki/Windows-1251) (ANSI codepage) is used for 8-bit files;
 * [`CP-866`](https://en.wikipedia.org/wiki/Code_page_866) (OEM codepage) is used for console output.

Windows have functions which help in these conversions:
[`MultiByteToWideChar`](https://msdn.microsoft.com/en-us/library/windows/desktop/dd319072%28v=vs.85%29.aspx) and 
[`WideCharToMultiByte`](https://msdn.microsoft.com/en-us/library/windows/desktop/dd374130%28v=vs.85%29.aspx).

This library provides a simple API for these functions.

## Usage

Put this in your `Cargo.toml`:

```toml
[dependencies]
local-encoding-ng = "*"
```

Or, better, use cargo-edit to add it with a correct version and use it to keep the version up-to-date.

For example:
```rust
use local_encoding_ng::{Encoding, Encoder};

fn main()
{
	println!("Unicode string: {}", Encoding::ANSI.to_string(b"ANSI string").unwrap());
	println!("Unicode string: {}", Encoding::OEM.to_string(b"OEM string").unwrap());
}
```
