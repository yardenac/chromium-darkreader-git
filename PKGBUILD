# Maintainer: Yardena Cohen <yardenack at gmail dot com>

gitname=darkreader
pkgname=chromium-${gitname}-git
pkgver=3254.f6d85c74
pkgrel=1
pkgdesc="Chromium extension to inverts brightness of web pages"
arch=('any')
url="https://github.com/${gitname}/${gitname}"
license=('MIT')
makedepends=(git nodejs-lts-fermium npm unzip ts-node)
checkdepends=(npm)
source=("git+${url}.git#tag=v4.9.28")
sha512sums=('SKIP')

pkgver() {
    cd "${srcdir}/${gitname}"
    local ver="$(git rev-list --count HEAD).$(git rev-parse --short HEAD)"
    printf "%s" "${ver//-/.}"
}
prepare() {
    cd "${srcdir}/${gitname}"
    npm install
}
check() {
    cd "${srcdir}/${gitname}"
    npm test
}
build() {
    cd "${srcdir}/${gitname}"
    npm run build
}
package() {
    mkdir -p "${pkgdir}/usr/share/chromium/${gitname}"
    unzip "${srcdir}/${gitname}/build.zip" -d "${pkgdir}/usr/share/chromium/${gitname}/"
}
