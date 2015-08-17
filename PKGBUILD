# Contributor: Juan Diego Tascon

pkgname=python2-txjsonrpc-git
pkgver=20120913
pkgrel=2
pkgdesc="JSON-RPC for Twisted"
arch=('any')
url="https://github.com/oubiwann/txjsonrpc"
license=('GPL3')
depends=('python2' 'python2-simplejson' 'twisted')
makedepends=('git' 'python2-distribute')

_gitroot="https://github.com/oubiwann/txjsonrpc.git"
_gitname="txjsonrpc"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
}

package() {
  cd "$srcdir/$_gitname-build"
  python2 setup.py install --root=${pkgdir} --optimize=1
}
