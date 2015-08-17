# Contributor: Andrew Gallant <andrew@pytyle.com>
# Maintainer: Andrew Gallant
pkgname=window-marker-git
pkgver=20110818
pkgrel=2
pkgdesc="Vim-like marking for jumping between windows."
arch=('any')
url="http://burntsushi.net/X11/window-marker"
license=('GPL')
groups=()
makedepends=('git')
depends=('python2>=2.7' 'xpybutil-git')
source=()
noextract=()
md5sums=()

_gitroot="git://github.com/BurntSushi/window-marker.git"
_gitname=window-marker
_gitbranch="master"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ]; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  if [ -d "$srcdir/$_gitname-build" ]; then
    rm -r "$srcdir/$_gitname-build"
  fi
  cp -r "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  msg "Clone finished, checking out branch $_gitbranch"
  git checkout $_gitbranch

  install -Dm644 LICENSE "$pkgdir/usr/share/doc/window-marker/LICENSE"
  install -Dm644 README "$pkgdir/usr/share/doc/window-marker/README"
  install -Dm755 window-marker "$pkgdir/usr/bin/window-marker"
}
