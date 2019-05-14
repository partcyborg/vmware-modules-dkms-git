# Maintainer: partcyborg <me@partcyb.org>
# Special thanks to mkubecek for creating the GitHub repository that this sources.

pkgname=vmware-host-modules-dkms-git
pkgver=1.0
pkgrel=2
pkgdesc="vmware-host-modules is a curated collection of patches to the propriatery vmware-host-modules kernel modules which come with vmware enabling them to successfully compile on any kernel version.  This package installs a dkms config to automatically build them at the appropriate tag for any given kernel version."
arch=("any")
license=("LGPL")
url="https://github.com/mkubecek/vmware-host-modules"
options=()
_dkmsname=vmware-host-modules
install=${pkgname}.install
makedepends=("dkms" "libsystemd" "git")
source=(
   "dkms.conf.in"
   "dkms.sh.in"
)
sha256sums=('SKIP' 'SKIP')
sha256sums=(
   "57984b4a196e78f7ec0c2557c03810c8c3cf6ae393ae725b97b8ebebcb02e6a1"
   "c4d6489274c779e418a5fd4d200c85f24903c7f116d2a6ea457fbc54cdd4c7f1"
)

_var_replace() {
   sed \
      -e "s/%PKGVER%/${pkgver}/" \
      -e "s/%DKMSNAME%/${_dkmsname}/" \
      "${srcdir}/$1" > "${srcdir}/$2"
}

prepare() {
   _var_replace dkms.conf.in dkms.conf
   _var_replace dkms.sh.in dkms.sh
}


package() {
   install -Dm644 "$srcdir/dkms.conf" "$pkgdir/usr/src/vmware-host-modules-${pkgver}/dkms.conf"
   install -Dm755 "$srcdir/dkms.sh" "$pkgdir/usr/src/vmware-host-modules-${pkgver}/dkms.sh"
}
