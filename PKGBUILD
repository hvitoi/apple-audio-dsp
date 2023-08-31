pkgname=apple-audio-dsp
_speakerpkgver=speakers-v0.2.0-1
_micpkgver=mic-v0.3.0
pkgver=141c47c
pkgrel=1
pkgdesc='Apple T2 MacbookPro16,1 speaker and microphone configuration'
arch=('any')
url='https://github.com/lemmyg/t2-apple-audio-dsp'
license=('MIT')
depends=(
  'pipewire'
  # speaker
  'calf'
  'lsp-plugins'
  # microphone
  'swh-plugins'
)
makedepends=('git')
optdepends=()
source=(
  "$url/archive/refs/tags/$_speakerpkgver.tar.gz"
  "$url/archive/refs/tags/$_micpkgver.tar.gz"
)
md5sums=('SKIP' 'SKIP')

pkgver() {
  echo $_speakerpkgver$_micpkgver | sha1sum | cut -c 1-7
}

package() {
  mkdir -p $pkgdir/etc/pipewire/pipewire.conf.d
  mkdir -p $pkgdir/usr/share/pipewire/devices/apple
  cp $srcdir/*$_speakerpkgver*/config/*.conf $pkgdir/etc/pipewire/pipewire.conf.d
  cp $srcdir/*$_speakerpkgver*/firs/*.wav $pkgdir/usr/share/pipewire/devices/apple
  cp $srcdir/*$_micpkgver*/config/*.conf $pkgdir/etc/pipewire/pipewire.conf.d
}
