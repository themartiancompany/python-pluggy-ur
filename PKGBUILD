# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Truocolo <truocolo@aol.com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg="pluggy"
pkgname="${_py}-${_pkg}"
pkgver=1.3.0
_commit=e13a58c5039bf7a8aa6a46a77244aea48b210510
pkgrel=1
pkgdesc="Plugin and hook calling mechanisms for python"
arch=(
  'any'
)
_http="https://github.com"
_ns="pytest-dev"
url="${_http}/${_ns}/${_pkg}"
license=(
  'MIT'
)
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
)
makedepends=(
  'git'
  "${_py}-setuptools-scm"
)
checkdepends=(
  "${_py}-pytest"
)
source=(
  "git+${url}.git#commit=${_commit}"
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
