# Maintainer: éclairevoyant

_pkgname=ocamlformat
pkgname="ocaml-$_pkgname"
pkgver=0.24.1
pkgrel=1
license=('MIT' 'custom:LGPL-2.1-OCaml')
arch=('x86_64')
pkgdesc="An OCaml Package"
url="https://github.com/ocaml-ppx/$_pkgname"
depends=('ocaml>=4.08' 'ocaml-menhir>=20201216' 'ocaml-csexp>=1.4.0' 'ocaml-cmdliner>=1.1.0' 'ocaml-uutf>=1.0.1' 'ocaml-stdio' 'ocaml-uuseg>=10.0.0' 'ocaml-re>=1.7.2' 'ocaml-fpath' 'ocaml-odoc-parser>=2.0.0' 'ocaml-odoc-parser<3.0.0' 'ocaml-ocp-indent' 'ocaml-fix' 'ocaml-either' 'ocaml-ocaml-version>=3.3.0')
makedepends=('dune>=2.8')
source=("$url/releases/download/$pkgver/$_pkgname-$pkgver.tbz")
options=('!strip')
sha256sums=('023425e9818f80ea50537b2371a4a766c149a9957d05807e88a004d2d5f441ce')
sha512sums=('753b6128be68042895202f99959b360ce954db6f82b19b83b4bb346761a8e9cfdfc2b4b25e2070e60601b555562e78f9ebb02760ff127464e0b66cedbddca304')

build() {
	cd $_pkgname-$pkgver
	dune build -p ocamlformat-rpc-lib,$_pkgname
}

package() {
	cd $_pkgname-$pkgver
	DESTDIR="$pkgdir" dune install $_pkgname --prefix "/usr" --libdir "/usr/lib/ocaml" --docdir "/usr/share/doc"
	install -dm755 "$pkgdir/usr/share/licenses/$pkgname/"
	ln -s /usr/share/doc/$_pkgname/LICENSE.md -t "$pkgdir/usr/share/licenses/$pkgname/"
}
