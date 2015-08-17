# Contributor: Guten <ywzhaifei@gmail.com>

pkgname=rtorrent-daemon-git
pkgver=20120207
pkgrel=1
pkgdesc="a daemon for rtorrent"
arch=("i686" "x86_64")
url="http://github.com/GutenYe/rtorrent-daemon"
license=("MIT-LICENSE")
groups=()
depends=("screen")
makedepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=("etc/conf.d/rtorrent")
options=()
install=
changelog=
source=()
md5sums=() 

_gitroot="git://github.com/GutenYe/rtorrent-daemon.git"
_gitname="rtorrent-daemon"

build() {
  cd ${srcdir}
  msg "Connecting to GIT server...."

  if [ -d ${_gitname}/.git ] ; then
    cd ${_gitname}

    # Change remote url to anongit
    if [ -z $( git branch -v | grep anongit ) ] ; then
        git remote set-url origin ${_gitroot}
    fi
    
    git pull origin
    msg "The local files are updated."
  else
    git clone ${_gitroot} ${_gitname}
  fi
  msg "GIT checkout done or server timeout"
}

package() {
  cd $srcdir/$_gitname

  mkdir -p $pkgdir/etc/conf.d
  mkdir -p $pkgdir/etc/rc.d

  cp conf.rtorrent $pkgdir/etc/conf.d/rtorrent
  cp rc.rtorrent $pkgdir/etc/rc.d/rtorrent
}


# vim:set ts=2 sw=2 et:
