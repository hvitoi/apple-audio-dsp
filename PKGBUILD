pkgname=apple-audio-dsp
pkgver=r55.0972911
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
  'noise-suppression-for-voice'
  'swh-plugins'
)
makedepends=('git')
optdepends=()
source=(
  "master::git+$url.git"
  "microphone::git+$url.git#branch=mic"
  "speaker::git+$url.git#branch=speakers_161"
)
md5sums=('SKIP' 'SKIP' 'SKIP')

pkgver() {
  cd master
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  sed -i 's/\/usr\/local\/lib\/ladspa\/librnnoise_ladspa.so/\/usr\/lib\/ladspa\/librnnoise_ladspa.so/g' $srcdir/*/config/*.conf
}

package() {
  mkdir -p $pkgdir/etc/pipewire/pipewire.conf.d
  mkdir -p $pkgdir/usr/share/pipewire/devices/apple
  cp $srcdir/microphone/config/*.conf $pkgdir/etc/pipewire/pipewire.conf.d
  cp $srcdir/speaker/config/*.conf $pkgdir/etc/pipewire/pipewire.conf.d
  cp $srcdir/speaker/firs/*.wav $pkgdir/usr/share/pipewire/devices/apple
}
