# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Mark Wagie <mark at manjaro dot org>

pkgname=manjaro-chrootbuild
pkgver=r320.d396ac3
pkgrel=1
pkgdesc="Build packages and buildlists in a chroot filesystem."
arch=('any')
url="https://gitlab.manjaro.org/tools/development-tools/manjaro-chrootbuild"
license=('GPL-3.0-or-later')
makedepends=('git')
conflicts=('manjaro-arm-chrootbuild')
replaces=('manjaro-arm-chrootbuild' 'manjaro-arm-chrootbuild-dev')
install="$pkgname.install"
_commit=d396ac3decca0c6c182123beb4ce688bba9de7e3
source=("git+$url.git#commit=${_commit}")
sha256sums=('7990d5fd73e711ca5ae9f517d83943743bcd42b4d47d36aa1b1e946b3135f6e3')

pkgver() {
  cd "$pkgname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short=7 HEAD)"
}

_install() {
  for f in $(ls $1/*.$2 | cut -d / -f 2); do
    install -Dm$3 $1/$f $pkgdir/$4/${f/.in/}
  done

}

package() {
cd "$pkgname"
  _install lib sh 644 /usr/lib/"$pkgname"
  _install bin in 755 /usr/bin
  _install data 'conf.*' 644 /etc/chrootbuild
  install -m644 data/build.sh "$pkgdir"/etc/chrootbuild
}
