# Lightly-ArchLinux
PKGBUILD file to build package from https://github.com/Bali10050/Lightly

### Usage to build the package

- run `curl -LO https://raw.githubusercontent.com/DeltaCopy/Lightly-ArchLinux/refs/heads/main/PKGBUILD`

#### Release tag changes

- update `pkgver` inside PKGBUILD to match the release tag name taken from https://github.com/Bali10050/Lightly/releases
- run `makepkg -g >> PKGBUILD ` to generate a SHA256SUM, this gets automatically added to the end of the file inside the array `sha256sums=()`

#### Build and install package

- run `makepkg -si` to build, and install the package
