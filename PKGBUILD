# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-pluggy
pkgname=(python-pluggy python2-pluggy)
pkgver=0.4.0
pkgrel=2
pkgdesc="Plugin and hook calling mechanisms for python"
arch=('any')
url="https://www.pluggypayments.com/docs/python"
license=('MIT')
makedepends=('python-setuptools' 'python2-setuptools')
checkdepends=('python-pytest-runner' 'python2-pytest-runner')
source=("https://pypi.io/packages/source/p/pluggy/pluggy-$pkgver.zip")
sha512sums=('1a6e28df05751767df1ac3dfac4c29ba0367f05ae9c8c6a7f5163bb53de36f90226ed18baedeb41bc8ca23504ca61a9b32ef907d3ec3fee7512bcdf45a56d19c')

prepare() {
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
  python setup.py ptr

  cd "$srcdir"/pluggy-$pkgver-py2
  python2 setup.py ptr
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
