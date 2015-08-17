# Maintainer: roger <roger _at_ rogerpc com ar>
# Contributor: dx <dx _at_ dxzone.com.ar>

pkgname=pycairo-xcb-git
pkgver=20120807
pkgrel=1
pkgdesc="Python bindings for the cairo graphics library with XCB enabled (git version)"
arch=(i686 x86_64)
license=('LGPL' 'MPL')
depends=('python2' 'cairo>=1.12' 'xorg-xpyb-git')
options=('!libtool')
url="http://www.cairographics.org/"
provides=("python2-cairo=1.10.1" 'pycairo' 'pycairo-git' 'pycairo-xcb')
makedepends=('git')
conflicts=('python2-cairo' 'pycairo' 'pycairo-git' 'pycairo-xcb')
_gitroot='git://git.cairographics.org/git/'
_gitname='py2cairo'

build() {
  export PYTHON=/usr/bin/python2

  if [ -d ${srcdir}/$_gitname ]; then
    cd $srcdir/$_gitname
    git pull
  else
    cd $srcdir
    git clone $_gitroot$_gitname
    cd $_gitname
  fi

  cd "${srcdir}/$_gitname"
  ./autogen.sh --enable-xcb --prefix=/usr
  make
}

package(){
  cd "${srcdir}/${_gitname}"
  make DESTDIR="${pkgdir}" install
  cd ${pkgdir}/usr/lib/python2.7/site-packages/
}
