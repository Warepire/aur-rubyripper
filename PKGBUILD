# Maintainer:
# Contributor: Alexander F Rødseth <xyproto@archlinux.org>
# Contributor: Maxime Gauduin <alucryd@gmail.com>
# Contributor: Dave Reisner <dreisner@archlinux.org>
# Contributor: Alexander Fehr <pizzapunk gmail com>

pkgname=rubyripper
pkgver=0.7.0rc1
pkgrel=11
pkgdesc='Secure audiodisc ripper'
arch=('any')
url='https://github.com/bleskodev/rubyripper'
license=('GPL3')
depends=('cdparanoia' 'gtk2' 'ruby-iconv')
# The configuration script will crash if ruby-gettext is installed without ruby-rake,
# ruby-gettex notes the dependency as optional.
optdepends=('ruby-gtk2: GTK+ GUI'
            'ruby-gettext: Localization support'
            'ruby-rake: Localization support'
            'cd-discid: Freedb support'
            'lame: MP3 encoding support'
            'vorbis-tools: Ogg Vorbis encoding support'
            'flac: FLAC encoding support'
            'wavegain: WAV ReplayGain support'
            'mp3gain: MP3 ReplayGain support'
            'vorbisgain: Ogg Vorbis ReplayGain support'
            'normalize: Normalization support'
            'cdrdao: Advanced TOC analysis')
source=("https://github.com/bleskodev/rubyripper/archive/v${pkgver}.tar.gz"
        "0001-configure-Make-update_mo-depend-on-LANG_SUPPORT.patch"
        "0001-gtk2-ripStatus-ruby-2.5-compliant-format-strings.patch")
sha256sums=('25c8d0c7a990d704a4df5737ffbce3e72ad0643dcbfc8633d5ddcda1ab76ea99'
            '825edfa9ccf34b9a51db4d96b99d20761c59e11c6a5a0bd1413ce5e665f6c70f'
            '64c51ee83421ef11710a6c9e99362fb1c6ba12adbf8f7000be93682833c1c45f')

prepare() {
  cd "${pkgname}-${pkgver}"

  patch -p1 -i "${srcdir}/0001-configure-Make-update_mo-depend-on-LANG_SUPPORT.patch"
  patch -p1 -i "${srcdir}/0001-gtk2-ripStatus-ruby-2.5-compliant-format-strings.patch"
}

build() {
  cd "${pkgname}-${pkgver}"

  ./configure --prefix='/usr' --enable-{cli,gtk2} \
    --ruby="$(ruby -e 'v = RbConfig::CONFIG["vendorlibdir"] ; v["/usr"] = ""; puts v')"
}

package() {
  make DESTDIR="$pkgdir" -C "$pkgname-$pkgver" install
}

# vim: ts=2 sw=2 et:
