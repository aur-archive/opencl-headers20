# Maintainer: Lukas Jirkovsky <l.jirkovsky@gmail.com>
# Contributor: Stéphane Gaudreault <stephane@archlinux.org>
# Contributor: Sylvain HENRY <hsyl20@yahoo.fr>

pkgname=opencl-headers20
pkgver=2.0.r28854
pkgrel=1
epoch=1
pkgdesc='OpenCL 2.0 (Open Computing Language) header files'
arch=('any')
url='http://www.khronos.org/registry/cl/'
license=('custom')
makedepends=('subversion')
optdepends=('libcl: OpenCL library')
provides=('opencl-headers=2:2.0' 'opencl-headers12=1:2.0')
conflicts=('opencl-headers')
source=("$pkgname::svn+https://cvs.khronos.org/svn/repos/registry/trunk/public/cl/api/2.0/")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  local ver="$(svnversion)"
  printf "2.0.r%s" "${ver//[[:alpha:]]}"
}

package() {
  cd "$srcdir/$pkgname"

  install -d -m 755 "$pkgdir"/usr/include/CL

  for h in $(ls -1 *.h *.hpp); do
     install -m 644 $h "$pkgdir"/usr/include/CL/
  done

  # extract the license from cl.h
  install -d -m 755 "$pkgdir"/usr/share/licenses/$pkgname
  sed '/#ifndef __OPENCL_CL_H/,$ d' cl.h > "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
