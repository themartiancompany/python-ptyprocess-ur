# Maintainer: Kyle Keen <keenerd@gmail.com>
# Contributor: Will Shanks <wsha dot code at g mail dot com>

pkgbase=python-ptyprocess
pkgname=(python-ptyprocess python2-ptyprocess)
_pkgname=ptyprocess
pkgver=0.5.2
pkgrel=1
pkgdesc="Run a subprocess in a pseudo terminal"
url="https://github.com/pexpect/ptyprocess"
arch=('any')
license=('ISC')
depends=('python')
makedepends=('python-setuptools' 'python2-setuptools')
source=("https://pypi.io/packages/source/p/$_pkgname/$_pkgname-$pkgver.tar.gz"
       'https://raw.githubusercontent.com/pexpect/ptyprocess/master/LICENSE')
md5sums=('d3b8febae1b8c53b054bd818d0bb8665'
         'cfdcd51fa7d5808da4e74346ee394490')

prepare() {
  cd "$srcdir"
  cp -r $_pkgname-$pkgver ${_pkgname}2-$pkgver
}

package_python-ptyprocess() {
  cd "$srcdir/$_pkgname-$pkgver"
  python3 setup.py install --root="$pkgdir/" --prefix=/usr --optimize=0
  install -Dm644 "$srcdir/LICENSE" "$pkgdir/usr/share/licenses/python-$_pkgname/LICENSE"
}

package_python2-ptyprocess() {
  depends=('python2')
  cd "$srcdir/${_pkgname}2-$pkgver"
  python2 setup.py install --root="$pkgdir/" --prefix=/usr --optimize=0
  install -Dm644 "$srcdir/LICENSE" "$pkgdir/usr/share/licenses/python2-$_pkgname/LICENSE"
}

