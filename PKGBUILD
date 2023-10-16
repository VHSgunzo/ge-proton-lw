# Maintainer: VHSgunzo <vhsgunzo.github.io>
pkgname='GE-Proton'
pkgver='8.19'
pkgrel='1'
pkgsrcname="${pkgname}${pkgver/./-}"
pkgdesc='GE-Proton for Runimage container'
arch=('x86_64')
url='https://github.com/GloriousEggroll/proton-ge-custom'
license=('MIT')
# provides=("$pkgname" 'wine-mono' 'wine-gecko')
provides=("$pkgname")
conflicts=("${provides[@]}")
source=("$pkgsrcname.tar.gz::https://github.com/GloriousEggroll/proton-ge-custom/releases/download/$pkgsrcname/$pkgsrcname.tar.gz")
sha256sums=('SKIP')

package() {
    install_dir="$pkgdir/usr/share/steam/compatibilitytools.d/$pkgsrcname"
    install -dm755 "$install_dir"
    cp -ar --no-preserve=ownership "$srcdir/$pkgsrcname"/* "$install_dir/"
    ln -sf "/usr/bin/cabextract" "$install_dir/files/bin/cabextract"
    sed -i "s|GE-Proton.*|$pkgsrcname|gi" "$install_dir/version"
    ln -sfr "$install_dir/version" "$install_dir/files/version"
#     mkdir -p "$pkgdir/usr/share/wine"
#     ln -sfr "$install_dir/files/share/wine/mono" "$pkgdir/usr/share/wine/mono"
#     ln -sfr "$install_dir/files/share/wine/gecko" "$pkgdir/usr/share/wine/gecko"
    for lib in d3d9-nine.dll.so latencyflex_layer.so ninewinecfg.exe.so
        do ln -sf "/usr/lib/wine/x86_64-unix/$lib" "$install_dir/files/lib64/wine/x86_64-unix/$lib"
    done
    for lib in d3d9-nine.dll latencyflex_layer.dll latencyflex_layer.dll.a latencyflex_wine.dll latencyflex_wine.dll.a ninewinecfg.exe
        do ln -sf "/usr/lib/wine/x86_64-windows/$lib" "$install_dir/files/lib64/wine/x86_64-windows/$lib"
    done
    for lib in d3d9-nine.dll.so ninewinecfg.exe.so
        do ln -sf "/usr/lib32/wine/i386-unix/$lib" "$install_dir/files/lib/wine/i386-unix/$lib"
    done
    for lib in d3d9-nine.dll ninewinecfg.exe
        do ln -sf "/usr/lib32/wine/i386-windows/$lib" "$install_dir/files/lib/wine/i386-windows/$lib"
    done
}
