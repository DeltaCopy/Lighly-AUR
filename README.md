# Lightly-ArchLinux
PKGBUILD file to build package from https://github.com/Bali10050/Lightly

### Usage to build the package

- clone this repository
- update `pkgver` inside PKGBUILD to match the release tag name taken from https://github.com/Bali10050/Lightly/releases
- run `makepkg -g` to generated the sha256sum and update the value inside the array `sha256sums=()`

### Installation

If you built the package successfully, a '.zst' file will be generated.

Use `sudo pacman -U <zst_file>` to install the package.
