# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Contributor: Truocolo <truocolo@aol.com>

_py="python"
_pkg="pluggy"
pkgname="${_py}-${_pkg}"
pkgver=1.3.0
_commit=e13a58c5039bf7a8aa6a46a77244aea48b210510
pkgrel=1
pkgdesc="Plugin and hook calling mechanisms for python"
arch=(
  'any'
)
url="https://github.com/pytest-dev/pluggy"
license=('MIT')
depends=(
  "${_py}"
)
makedepends=(
  'git'
  "${_py}-setuptools-scm"
)
checkdepends=(
  "${_py}-pytest"
)
source=(
  "git+https://github.com/pytest-dev/${_pkg}.git#commit=${_commit}"
)
sha512sums=(
  'SKIP'
)

build() {
  cd \
    "${_pkg}"
  "${_py}" \
    setup.py \
      build
}

check() {
  cd \
    "${_pkg}"
  PYTHONPATH="$PWD"/src \
    pytest
}

package() {
  cd \
    "${_pkg}"
  "${_py}" \
    setup.py \
      install \
        -O1 \
	--root="${pkgdir}"
  install \
    -Dm644 LICENSE \
    -t "${pkgdir}"/usr/share/licenses/${pkgname}/
}

# vim:set sw=2 sts=-1 et:
