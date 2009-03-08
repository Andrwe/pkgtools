# Maintainer: Daenyth <Daenyth+Arch AT gmail DOT com>
# Contributor: Daenyth <Daenyth+Arch AT gmail DOT com>
pkgname=pkgtools
pkgver=13
pkgrel=2
pkgdesc="A collection of scripts for Arch Linux packages"
arch=(any)
url="http://bbs.archlinux.org/viewtopic.php?pid=384196"
license=('GPL')
source=(http://github.com/Daenyth/pkgtools/tarball/v$pkgver)
backup=('etc/pkgtools/newpkg.conf' 'etc/pkgtools/pkgfile.conf' 'etc/pkgtools/spec2arch.conf')
install=pkgtools.install
provides=(newpkg pkgfile)
optdepends=('cron: For pkgfile --update entry')
md5sums=('43b47bb49176c3da14b725b832109eb8')


build() {
  cd "$srcdir/Daenyth-$pkgname-*"

  # Common fucntions needed by all scripts
  install -Dm644 "other/functions"         "${pkgdir}/usr/share/pkgtools/functions"

  # newpkg
  install -Dm755 "scripts/newpkg"          "${pkgdir}/usr/bin/newpkg"
  install -Dm644 "confs/newpkg.conf"       "${pkgdir}/etc/pkgtools/newpkg.conf"

  # pkgfile
  install -d "$pkgdir/var/cache/pkgtools/lists/"
  install -Dm755 "scripts/pkgfile"         "${pkgdir}/usr/bin/pkgfile"
  install -Dm644 "confs/pkgfile.conf"      "${pkgdir}/etc/pkgtools/pkgfile.conf"
  install -Dm744 "other/pkgfile.cron"      "${pkgdir}/etc/cron.daily/pkgfile"
  # Loads shell hooks
  install -Dm755 "other/pkgfile-hook.sh"   "${pkgdir}/etc/profile.d/pkgfile-hook.sh"
  install -Dm644 "other/pkgfile-hook.zsh"  "${pkgdir}/usr/share/pkgtools/pkgfile-hook.zsh"
  install -Dm644 "other/pkgfile-hook.bash" "${pkgdir}/usr/share/pkgtools/pkgfile-hook.bash"

  # spec2arch
  install -Dm755 "scripts/spec2arch"       "${pkgdir}/usr/bin/spec2arch"
  install -Dm644 "confs/spec2arch.conf"    "${pkgdir}/etc/pkgtools/spec2arch.conf"
  install -Dm644 "confs/spec2arch.8"       "${pkgdir}/usr/share/man/man8/spec2arch.8"
  install -Dm644 "confs/spec2arch.conf.5"  "${pkgdir}/usr/share/man/man5/spec2arch.conf.5"
}

# vim:set ts=2 sw=2 et:
