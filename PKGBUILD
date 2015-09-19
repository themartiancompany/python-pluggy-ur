# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-pluggy
pkgname=(python-pluggy python2-pluggy)
pkgver=0.3.0
pkgrel=2
pkgdesc="Plugin and hook calling mechanisms for python"
arch=('any')
url="https://www.pluggypayments.com/docs/python"
license=('MIT')
makedepends=('python-setuptools' 'python2-setuptools')
checkdepends=('python-pytest' 'python2-pytest')
source=("https://pypi.python.org/packages/source/p/pluggy/pluggy-$pkgver.tar.gz")
sha512sums=('0c4deb74f8d5d5584cd347fcfdb694e54e4beb17dba153e4cdd9da56ae1626211c08e1d4452034a1adf5b4f9fea5f3908a0bf8eaa661cf98fb5a4d61f16e4c18')

prepare() {
  cp -a pluggy-$pkgver{,-py2}
}

build() {
  cd pluggy-$pkgver
  python setup.py build

  cd ../pluggy-$pkgver-py2
  python2 setup.py build
}

check() {
  cd pluggy-$pkgver
  PYTHONPATH="$PWD/build/lib:$PYTHONPATH" py.test

  cd ../pluggy-$pkgver-py2
  PYTHONPATH="$PWD/build/lib:$PYTHONPATH" py.test2
}

package_python-pluggy() {
  depends=('python')

  cd pluggy-$pkgver
  python setup.py install -O1 --root "${pkgdir}"

  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

package_python2-pluggy() {
  depends=('python2')

  cd pluggy-$pkgver-py2
  python2 setup.py install -O1 --root "${pkgdir}"

  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
