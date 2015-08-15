# Maintainer: Pi3R1k <pierrick.brun @ gmail com
# Contributor: Gordin <9ordin @t gmail dot com>

pkgname=firefox-beta-fr
pkgdesc='Standalone web browser from mozilla.org, Aurora build, French'
url='http://www.mozilla.org/projects/firefox'
pkgver=18.0b4
pkgrel=1
arch=('i686' 'x86_64')
license=('MPL' 'GPL' 'LGPL')
source=('firefox-beta.desktop' 'firefox-beta-safe.desktop')
sha1sums=('78b7fe5ea5275f269eb96e31b6edd428b83f167a' '5014d94449128a3fab0b80b8e469e125be1e5923')
depends=('desktop-file-utils' 'libxt' 'mime-types' 'nss' 'alsa-lib' 'libnotify')
conflicts=('firefox-beta')
provides=('firefox-beta')
install=firefox.install


package() {
  FX_SRC="firefox-${pkgver}.tar.bz2"
  FX_SRC_URI="http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/${pkgver}/linux-${CARCH}/fr/${FX_SRC}"

  msg "Downloading..."
  wget -N ${FX_SRC_URI}
  msg "Extracting..."
  bsdtar -x -f ${FX_SRC}
  msg "Packaging..."

#   uncomment this line to remove these
#   rm -rf firefox/{extensions,plugins,searchplugins}

  mkdir -p "${pkgdir}"/{usr/{bin,share/{applications,pixmaps}},opt}
  cp -r firefox "${pkgdir}/opt/firefox-${pkgver}"

  ln -s /opt/firefox-${pkgver}/firefox "${pkgdir}/usr/bin/firefox-beta"
  install -m644 "${srcdir}"/{firefox-beta.desktop,firefox-beta-safe.desktop} "${pkgdir}/usr/share/applications/"
  install -m644 "${srcdir}/firefox/icons/mozicon128.png" "${pkgdir}/usr/share/pixmaps/firefox-beta-icon.png"
}
