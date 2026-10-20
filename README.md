# Windows HEIC Extension

A free, open-source project to bring native HEIC photo support to Windows, without requiring users to buy the Microsoft Store HEVC extension.

**Status: planning stage. No working codec, installer, or downloadable release exists yet.**

## Goals

- Display `.heic` and `.heif` thumbnails in File Explorer.
- Let compatible Windows applications decode photos through Windows Imaging Component (WIC).
- Process images locally, without uploading personal photos.
- Provide a straightforward installer and clean uninstall.

Initial target: Windows 11 x64. ARM64 and other Windows versions can follow after validation. Windows Photos compatibility must be tested; it is not guaranteed by installing a WIC codec.

## Proposed approach

Use C++ and CMake for a native WIC decoder backed by an existing open-source HEIF/HEVC decoder. Evaluate [libheif](https://github.com/strukturag/libheif) with an HEVC decoding backend before choosing and pinning dependencies. No decoder is bundled yet.

See [the roadmap](docs/ROADMAP.md) for implementation milestones and acceptance criteria.

## Development

This repository currently contains project documentation only. Build and install instructions will be added with the first decoding prototype. Do not register or install anything from this repository yet.

Contributions should keep image processing offline, bound memory use for untrusted files, and include evidence for any compatibility claims. Use synthetic or explicitly redistributable test images; do not commit private iPhone photos.

## Licensing

Original project code and documentation are MIT licensed. Third-party decoder licenses and distribution requirements must be documented before bundling dependencies; the MIT license does not cover those libraries or grant third-party patent rights.

## Technical references

- [Microsoft: Windows Imaging Component overview](https://learn.microsoft.com/en-us/windows/win32/wic/-wic-about-windows-imaging-codec)
- [Microsoft: creating a WIC decoder](https://learn.microsoft.com/en-us/windows/win32/wic/-wic-creating-decoder)
- [Microsoft: codec installation and registration](https://learn.microsoft.com/en-us/windows/win32/wic/-wic-codecinstallandreg)
- [libheif source and dependency documentation](https://github.com/strukturag/libheif)
