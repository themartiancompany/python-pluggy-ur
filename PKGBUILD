# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-pluggy
pkgname=(python-pluggy python2-pluggy)
pkgver=0.7.1
pkgrel=1
pkgdesc="Plugin and hook calling mechanisms for python"
arch=('any')
url="https://www.pluggypayments.com/docs/python"
license=('MIT')
makedepends=('python-setuptools-scm' 'python2-setuptools-scm')
checkdepends=('python-pytest-runner' 'python2-pytest-runner')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/pytest-dev/pluggy/archive/$pkgver.tar.gz")
sha512sums=('0b5e905bffeeb7627fa0c20203194c5b648376605c28d00fa3299bbfba4783901bb1b49d0279cd79474bfb015e0dfb7cdb9baf1673bb6f085ba08d13534a1fa4')

prepare() {
  cp -a pluggy-$pkgver{,-py2}

  export SETUPTOOLS_SCM_PRETEND_VERSION=$pkgver
}

build() {
  cd "$srcdir"/pluggy-$pkgver
  python setup.py build

  cd "$srcdir"/pluggy-$pkgver-py2
  python2 setup.py build
}

check() {
  cd "$srcdir"/pluggy-$pkgver
  python setup.py pytest

  cd "$srcdir"/pluggy-$pkgver-py2
  python2 setup.py pytest
}

package_python-pluggy() {
  depends=('python')

  cd pluggy-$pkgver
  python setup.py install -O1 --root "$pkgdir"

  install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

package_python2-pluggy() {
  depends=('python2')

  cd pluggy-$pkgver-py2
  python2 setup.py install -O1 --root "$pkgdir"

  install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
