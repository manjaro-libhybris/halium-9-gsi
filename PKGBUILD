# Maintainer: Bardia Moshiri <fakeshell@bardia.tech>

pkgname=halium-9-gsi
pkgver=0.1
pkgrel=1
pkgdesc="Halium rootfs for Android 9"
arch=('aarch64')
url="https://github.com/manjaro-libhybris/halium-9-gsi"
license=('custom')
provides=('halium-gsi')
conflicts=('halium-10-gsi' 'halium-11-gsi')
depends=('lxc')
makedepends=('wget' 'tar')
options=()

package() {
  LATEST=$(wget -q -O - https://ci.ubports.com/job/UBportsCommunityPortsJenkinsCI/job/ubports%252Fporting%252Fcommunity-ports%252Fjenkins-ci%252Fgeneric_arm64/job/main/api/json | awk -F 'org.jenkinsci.plugins.workflow.job.WorkflowRun' '{print $2}' | cut -d '"' -f7)
  wget $LATEST/artifact/halium_halium_arm64.tar.xz

  tar -xf halium_halium_arm64.tar.xz

  mkdir -p ${pkgdir}/var/lib/lxc/android/

  install -m644 "$srcdir"/system/var/lib/lxc/android/android-rootfs.img "$pkgdir"/var/lib/lxc/android/android-rootfs.img
}
