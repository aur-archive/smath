# Contributor: Anton Bazhenov <anton.bazhenov at gmail>
# Maintainer: Stefan Husmann <stefan-husmann@t-online.de>
# Maintainer: ximeg <ximeg@tomcity.net>
# Maintainer: desperat <c2h5ohzh2@o2.pl>
# Maintainer: Mihai Coman <mihai@m1x.ro>

pkgname=smath
pkgver=0.97
pkgrel=1
pkgdesc="A mathematical program with many features and paper-like interface, similar to Mathcad"
arch=('i686' 'x86_64')
url="http://smath.info"
license=('CCPL')
groups=('math')
depends=('mono')
install=smath.install
backup=(opt/$pkgname/settings.inf)
source=("https://www.dropbox.com/s/cmdomnldqnlsuiz/SMathStudioDesktop.0_97_5346.Mono.tar.gz" 
	"smath.desktop" 
	"http://dl.dropbox.com/u/2776506/SMathStudioLogo256.png")
md5sums=('cb922fa31fca89d347df6468d421eb52'
         'af70c1bfb5bcdaab7f952339ebb2435e'
         'ed3720462decbcfa63df5c9d04fb03f9')

package() {
  cd "$srcdir"
  # install program
  install -m755 -d "$pkgdir"/opt/$pkgname/{book,examples,lang,entries,plugins,snippets}
  install -m644 -t "$pkgdir"/opt/$pkgname/book book/*
  install -m644 -t "$pkgdir"/opt/$pkgname/examples examples/*
  install -m644 -t "$pkgdir"/opt/$pkgname/lang lang/*
  install -m644 -t "$pkgdir"/opt/$pkgname *.{dll,exe}
  install -m644 -t "$pkgdir"/opt/$pkgname/entries entries/*
  install -m644 -t "$pkgdir"/opt/$pkgname/plugins plugins/*
  install -m644 -t "$pkgdir"/opt/$pkgname/snippets snippets/*

  # create settings file
  touch "$pkgdir"/opt/$pkgname/settings.inf
  chmod 664 "$pkgdir"/opt/$pkgname/settings.inf

echo "#!/bin/sh
cd /opt/smath
mono SMathStudio_Desktop.exe \"$@\"
" > ../$pkgname.sh

  # install launcher
  install -Dm755 ../$pkgname.sh "$pkgdir"/usr/bin/$pkgname
  install -Dm644 "${srcdir}/smath.desktop" "${pkgdir}/usr/share/applications/smath.desktop"
  install -Dm644 "${srcdir}/SMathStudioLogo256.png" "${pkgdir}/usr/share/pixmaps/smath.png"

}
