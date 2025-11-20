# pyssf

`pyssf` is a Python library for working with SSF (Standard Spreadsheet Format)
numbers, providing robust formatting and parsing capabilities.

## Features

- **Number Formatting:** Format numbers according to SSF specifications.

## Installation

### Using uv (Recommended)

clone the repo, then run `uv sync`

## Precompiled Deno Module

The deno interface for calling ssf.js has been pre-compiled via:
```
deno compile --unstable-detect-cjs --target x86_64-pc-windows-msvc --output vendor/ssf_win vendor/main.ts

deno compile --unstable-detect-cjs --target aarch64-apple-darwin --output vendor/ssf_aarm vendor/main.ts

deno compile --unstable-detect-cjs --target x86_64-unknown-linux-gnu --output vendor/ssf_linux vendor/main.ts
```

This tool does not require deno to be installed by utilizing the pre-compiled modules. If you want to run ssf.js via deno, pass `deno_script_path=vendor/main.ts` when initializing an SSFFormatter instance.

### Validate bin Hash:
**ssf_aarm** `shasum -a 256 ssf_aarm` =
`49a61674c179ee6a9edf343eb07ae8a8f3d2c66c3de47a1acedaddc1838c390c`

**ssf_win** `certutil -hashfile -SHA256 ssf_win` =
`bf90aaf4fb4b71af8d8b8dbeceb37f5692c9ad4c61f7f978a719701c11942eac`

**ssf_linux** `sha256sum ssf_linux` =
`dad0d14e07dbe19d45ff5a7ef5cc8a86d1221da133c773dcaecf8434b59aae3e`

## Usage

```python
from pyssf import SSFFormatter

formatter = SSFFormatter()
formatted_value = formatter.format("0#.0", 1.556)
print(f"{formatted_value=}") # >>> formatted_value='01.6'
```

## License

This project is licensed under the Apache License, Version 2.0 - see the
[LICENSE](LICENSE) file for details.

## Third-Party Components

This project utilizes `ssf.js`, which is also licensed under the Apache License,
Version 2.0. A modification has been made to the original `ssf.js` file
(`vendor/main.ts`) to export its functionality using ES module format to
facilitate integration with this project.
