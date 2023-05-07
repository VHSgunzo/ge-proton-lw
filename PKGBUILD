# Maintainer: VHSgunzo <vhsgunzo.github.io>
pkgname='GE-Proton'
pkgver='8.2'
pkgrel='1'
pkgsrcname="${pkgname}${pkgver/./-}"
pkgdesc='Lutris Wine GE-Proton for Runimage container'
arch=('x86_64')
url='https://github.com/GloriousEggroll/proton-ge-custom'
license=('MIT')
provides=("$pkgname")
conflicts=("$pkgname")
source=("$pkgsrcname.tar.gz::https://github.com/GloriousEggroll/proton-ge-custom/releases/download/$pkgsrcname/$pkgsrcname.tar.gz")
sha256sums=('SKIP')

package() {
    install_dir="$pkgdir/usr/share/steam/compatibilitytools.d/$pkgsrcname"
    install -dm755 "$install_dir"
    cp -ar --no-preserve=ownership "$srcdir/$pkgsrcname"/* "$install_dir/"
    ln -sf "$pkgdir/usr/bin/cabextract" "$install_dir/files/bin/cabextract"
}
