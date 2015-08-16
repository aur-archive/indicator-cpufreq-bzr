# Maintainer: Que Quotion <quequotion@mailinator.com>
# Contributor: Xiao-Long Chen <chenxiaolongcxl.epac.to>

pkgname=indicator-cpufreq-bzr
pkgver=r95
pkgrel=1
pkgdesc="CPU frequency indicator (bzr version)"
arch=('i686' 'x86_64')
url="https://launchpad.net/indicator-cpufreq"
license=('GPL')
groups=('unity-extra')
depends=('cpupower' 'libappindicator3' 'python2' 'python2-dbus' 'python2-gobject' 'pygtk')
makedepends=('python2-distutils-extra')
provides=('indicator-cpufreq' 'indicator-cpufreq-bzr')
conflicts=('indicator-cpufreq' 'indicator-cpufreq-bzr')
source=("bzr+lp:indicator-cpufreq"
        'indicator-cpufreq.rules'
        '0001_Use_cpupower.patch')
sha512sums=('SKIP'
            '16997d88f7253fb1b7f0c4a7bd9e87597b6f2b859e531f038f1bde47fa531c683e44fd4b3aacdc58f75a086e9f7e5dba37b369007220b70b689d9ecad89ea391'
            '8aad00c00a95d71f221647263422eef89a0207bdb55d883520f3871f28551c316860560207c96144e22dda2ab5f5fc9b8c7bfa0fc642283de160bfd61458b8c0')

pkgver() {
  cd indicator-cpufreq

  printf "r%s" "$(bzr revno)"
}

prepare() {
  cd "${srcdir}/indicator-cpufreq"

  patch -Np1 -i "${srcdir}/0001_Use_cpupower.patch"
}

package() {
  cd "${srcdir}/indicator-cpufreq"
  python2 setup.py install --root="${pkgdir}/" --optimize=1

  install -dm700 "${pkgdir}/usr/share/polkit-1/rules.d/"
  install -m644 "${srcdir}/indicator-cpufreq.rules" \
    "${pkgdir}/usr/share/polkit-1/rules.d/"
}
