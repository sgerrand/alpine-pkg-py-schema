# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
pkgname=py-schema
_pkgname=schema
pkgver=0.6.8
pkgrel=0
pkgdesc="Schema is a library for validating Python data structures"
url="https://github.com/keleshev/$_pkgname"
arch="noarch"
license="MIT"
depends="python"
makedepends="py-setuptools pytest python2-dev python3-dev"
install=""
subpackages="py2-${pkgname#py-}:_py2 py3-${pkgname#py-}:_py3"
source="$pkgname-$pkgver.tar.gz::https://github.com/keleshev/$_pkgname/archive/v$pkgver.tar.gz"
builddir="$srcdir/$_pkgname-$pkgver"

build() {
	cd "$builddir"
	python2 setup.py build
	python3 setup.py build
}

check() {
	cd "$builddir"
	python2 setup.py test
	python3 setup.py test
}

package() {
	mkdir -p "$pkgdir"
}

_py() {
	local python="$1"
	pkgdesc="$pkgdesc ${python#python}"
	depends="$depends $python"
	subpkgarch="all"
	install_if="$pkgname=$pkgver-r$pkgrel $python"

	cd "$builddir"
	$python setup.py install --prefix=/usr --root="$subpkgdir"
}

_py2() {
	replaces="$pkgname"
	depends="${depends//py-/py2-}"
	_py python2
}

_py3() {
	depends="${depends//py-/py3-}"
	_py python3
}

sha512sums="3de2d7ef5eca8d1b333c1b8e3535d3522ddf8f416d1fb5b2e75f133ae5eb14226b1924c8c367a60381621ed55d0e626bd75fc622462badc44974ebc395929dac  py-schema-0.6.8.tar.gz"
