# Maintainer: Andreas Søvik <arsovik@gmail.com>
# Forked from https://aur.archlinux.org/packages/dropbox/ | Maintained by: Massimiliano Torromeo <massimiliano.torromeo@gmail.com> (Outdated at date of this PKGBUILD)

pkgname=dropbox
pkgver=1.6.17
pkgrel=1
pkgdesc="A free service that lets you bring your photos, docs, and videos anywhere and share them easily."
arch=("x86_64")
url="http://www.dropbox.com"
license=(custom)
depends=("dbus-glib" "gtk2" "libsm")
conflicts=("dropbox-experimental")
options=('!strip' '!upx')

_source_arch="x86_64" # only supporting this badboy

sha256sums=("d276376ebc7a062a7280a76afbd19c7c6fa0e0434229389174282458d682d266"
            "bd443ed290e3b6b1f6a4e2ff56107ac3343e32267c4af4a1b8b6ea8c03183904"
            "b9e020c378c318e72857bb6cd859c74e8da1300f34cee5bfec89c4f7a89770a9")

source=("https://dl-web.dropbox.com/u/17/${pkgname}-lnx.${_source_arch}-${pkgver}.tar.gz"
        "dropbox.service"
        "terms.txt")

build() {
    install -d "$pkgdir/opt"
    cp -R "$srcdir/.dropbox-dist" "$pkgdir/opt/dropbox"

    find "$pkgdir/opt/dropbox/" -type f -exec chmod 644 {} \;
    chmod 755 "$pkgdir/opt/dropbox/dropboxd"
    chmod 755 "$pkgdir/opt/dropbox/dropbox"

    install -d "$pkgdir/usr/bin"
    ln -s "/opt/dropbox/dropboxd" "$pkgdir/usr/bin/dropboxd"

    install -Dm644 "$srcdir/dropbox.service" "$pkgdir/usr/lib/systemd/system/dropbox@.service"
}

