# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-pluggy
pkgname=(python-pluggy python2-pluggy)
pkgver=0.6.0
_commit=607862cac33f62826e2ee710e3e5a71bd794af4a
pkgrel=1
pkgdesc="Plugin and hook calling mechanisms for python"
arch=('any')
url="https://www.pluggypayments.com/docs/python"
license=('MIT')
makedepends=('python-setuptools' 'python2-setuptools')
checkdepends=('python-pytest-runner' 'python2-pytest-runner')
source=("$pkgbase-$_commit::https://github.com/pytest-dev/pluggy/archive/$_commit.tar.gz")
sha512sums=('697927dde4da0c0faf9c7de1342b9c452667e481b40f9bbef836064cfc37ef917c64fcf2ca158a6cc00a12853387d6c0adec708a3ccbfe789da480fcae6fd566')

prepare() {
  mv pluggy-{$_commit,$pkgver}
  cp -a pluggy-$pkgver{,-py2}
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
