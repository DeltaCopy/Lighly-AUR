# Lightly-ArchLinux
PKGBUILD file to build package from https://github.com/Bali10050/Lightly

### Usage to build the package

- Run `curl -LO https://raw.githubusercontent.com/DeltaCopy/Lightly-ArchLinux/refs/heads/main/PKGBUILD`

#### Building from a specific release tag

- Update `pkgver` inside PKGBUILD to match the release tag name taken from https://github.com/Bali10050/Lightly/releases
- Run `makepkg -g >> PKGBUILD ` to generate a SHA256SUM, which is automatically added to the end of the file inside the array `sha256sums=()`

#### Build and install package

- Run `makepkg -si` to build, and install the package

## Pending activities

- [ ] Migrate PKGBUILD over to the AUR once the package name is finalized
