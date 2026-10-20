# Implementation roadmap

## 1. Standalone decoding prototype

Evaluate libheif and its HEVC decoder backend. Pin dependencies and document their licenses. Build a small C++ command-line tool before adding shell integration.

Acceptance: decode redistributable iPhone-style HEIC samples into inspectable pixels; verify dimensions, orientation, and color on the initial SDR path. Reject truncated and malformed input cleanly. Set explicit image dimension and allocation limits. Document unsupported HDR, auxiliary images, and multi-image features.

## 2. WIC decoder

Implement the native COM decoder and frame interfaces, pixel copying, format detection, and registration metadata. Keep HEIF parsing and decoding behind a small adapter.

Acceptance: a separate WIC test application discovers the codec and decodes the same samples. Exercise COM lifetime, stream behavior, stride and buffer validation, and repeated decoding. Document behavior when another HEIF codec is already installed.

## 3. Explorer integration

Test thumbnail discovery through WIC on a clean Windows 11 x64 virtual machine, both with and without Microsoft's optional HEIF/HEVC components. Add a dedicated thumbnail provider only if WIC integration proves insufficient.

Acceptance: Explorer shows correct thumbnails without crashes or hangs; malformed files fail safely. Record exact Windows versions, installed codecs, and test results. Test Windows Photos separately and publish the observed compatibility.

## 4. Installation and release

Package the codec and required runtime libraries. Include dependency notices, reproducible build instructions, and installation/uninstallation steps. Evaluate signing before public binary releases.

Acceptance: install, upgrade, and uninstall in a disposable VM. Remove only this project's registration and preserve existing associations and codecs. Verify no dependency on the paid Store HEVC extension in the supported test configuration.

## 5. Broader support

Evaluate ARM64, additional Windows versions, HDR/color profiles, and additional HEIF variants against explicit test fixtures. Extend compatibility claims only after testing.
