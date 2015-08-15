#Maintainer: Alex Ferrando <alferpal@gmail.com>
# Contributor: Archan Paul <arp@archan.org>

pkgname=eclipse-darkjuno
pkgver=1.0.0.201207121019
pkgrel=1
pkgdesc="Dark theme for eclipse juno"
arch=('i686' 'x86_64')
url="https://github.com/eclipse-color-theme/eclipse-ui-themes"
license=('EPL')
depends=('eclipse>=4.2' )
source=("https://github.com/downloads/rogerdudler/eclipse-ui-themes/com.github.eclipsecolortheme.themes_1.0.0.201207121019.zip")

md5sums=('14d15340bb43f685cf47bc71f72f8cbe')

package() {
  _dest=${pkgdir}/usr/share/eclipse/dropins/${pkgname/eclipse-}/eclipse

  cd ${srcdir}
  
  # Features
  find features -type f | while read _feature ; do
    echo ${_feature}
    if [[ ${_feature} =~ (.*\.jar$) ]] ; then
      install -dm755 ${_dest}/${_feature%*.jar}
      cd ${_dest}/${_feature/.jar}
      jar xf ${srcdir}/${_feature} || return 1
    else
      install -Dm644 ${_feature} ${_dest}/${_feature}
    fi
  done

  # Plugins
  find plugins -type f | while read _plugin ; do
    install -Dm644 ${_plugin} ${_dest}/${_plugin}
  done
}

