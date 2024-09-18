# Maintainer: Nico <d3sox at protonmail dot com>
# Contributor: Sefa Eyeoglu <contact@scrumplex.net>
# Modified: DeltaCopy <https://github.com/DeltaCopy>
# Description: Builds Lightly from src: https://github.com/Bali10050/Lightly

# basic info
pkgname="lightly-qt6"
pkgver=0.5.1 # change this to match the name of the release tag you want to build from
pkgrel=1
pkgdesc="Modern style for KDE/Qt applications"
url="https://github.com/Bali10050/lightly"
arch=('x86_64' 'aarch64')
license=("GPL-2.0-or-later")
pkgdir="$srcdir/fakeinstall_kf6"

makedepends=(
  'cmake'
  'extra-cmake-modules'
  'git'
)

options=(!emptydirs !debug)

source=(
    "${pkgname}.git::git+${url}.git#tag=v${pkgver//_/-}"
)

# use makepkg -g to generate the sha256sum for the release tag
sha256sums=(
  '86790e88ac2275cbf0bb398c143716f1f80014927861765c89b3e8dbea0387d7'
)

build() {
  prepare
  build
  package
}

# KF6/Qt6
depends_kf6=(
  'frameworkintegration'
  'hicolor-icon-theme'
  'kcmutils'
  'kcolorscheme'
  'kconfig'
  'kcoreaddons'
  'kdecoration'
  'kguiaddons'
  'kiconthemes'
  'kwindowsystem'
  'qt6-declarative'

  ## implicit
  #ki18n
  #kwidgetsaddons
  #qt6-base
)
depends=("${depends_kf6[@]}")

provides=(
  lightly-kf6
  lightly-qt6
  lightly-qt6-git
)

conflicts=(
  lightly-kf6
  lightly-qt6
  lightly-qt6-git
)

prepare() (
  cd "$pkgname.git"
  git checkout -f qt6
  #patch -Np1 -F100 -i ../qt6-missing-config.patch
)

build() (
  local cmake_options=(
    -B build_kf6
    -S "$pkgname.git"
    -DBUILD_TESTING=OFF
    -Wno-dev
  )

  cmake "${cmake_options[@]}"
  cmake --build build_kf6/kdecoration/config/
  cmake --build build_kf6
)

package() (
  install -dm755 "$pkgdir.git"
  DESTDIR="$pkgdir" cmake --install build_kf6
  rm -rf "$pkgdir/usr/lib/cmake"
)

package_lightly-kf6-git() {
  mv "$pkgdir.git"/* "$pkgdir.git/"
  chmod u=rwX,g=rX,o=rX -R "$pkgdir.git"
}

