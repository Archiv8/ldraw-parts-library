#!/bin/bash

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <archiv8@artisteducator.com>
# Contributor: Ross Clark <archiv8@artisteducator.com>

pkgname=ldraw-parts-library
pkgver=20220329
pkgrel=1
pkgdesc="A collection of LDraw-format CAD files representing many of LEGO bricks produced"
arch=(any)
url="http://www.ldraw.org/parts/latest-parts.html"
license=("CCPL: cc-by-2.0")
options=(!strip)
source=(
  "ldraw-parts-${pkgver}.zip::http://www.ldraw.org/library/updates/complete.zip"
  "LDConfig-${pkgver}.ldr::http://www.ldraw.org/library/official/LDConfig.ldr"
  "ldraw-parts-library.sh"
  "license")
sha512sums=('897803a357d98004407abb98bf28be1f1aca76904bed70498c3640d7aac116a0fbd3546a741bd5274daa642fc6be09dcbe5bfb53408b150b85d7a1138ea7ea62'
            '0dab0e6589141dd1a1bcc461c9e711977fc3302c82bfbd5deffdb97bddeed357da974fe3f191e37e52a14691651c7aa0c9590476c5eb8675e1bf0132a3c230e5'
            '42f4e214647fc4181b1f10d0ccd3a2f29d65665812877492d1b048ebc4442e671a59b4c4cc3b0b1376dd3c10074663a02e28222b9606ae7e7707ee87075569be'
            '543b505b9665eaa04e6baa55103d278e88e455133f059b350ca99d109cec58cc6373855ce25e54b69fa227bea7efc4e0d5f63dc514dd05b495d5027ab583d19e')

pkgver() {
  echo $(date -uI|sed "s,-,,g")
}

package() {
  cd "${srcdir}/ldraw/"

  # Install data
  mkdir -p                      "${pkgdir}/usr/share/ldraw"
  cp ../LDConfig-${pkgver}.ldr  "${pkgdir}/usr/share/ldraw/"
  mv p                          "${pkgdir}/usr/share/ldraw/"
  mv parts                      "${pkgdir}/usr/share/ldraw/"

  # Fix permissions
  find "${pkgdir}/usr/share/ldraw" -type f -exec chmod 644 {} +
  find "${pkgdir}/usr/share/ldraw" -type d -exec chmod 755 {} +

  # Install the old version 2.0 CC-by license
  install -D -m644 ../license                "${pkgdir}/usr/share/licenses/${pkgname}/license"

  install -D -m755 ../ldraw-parts-library.sh "${pkgdir}/etc/profile.d/ldraw-parts-library.sh"
}

#sha512sums=("SKIP"
#         "SKIP"
#         "2acda6add7ed39994a710bd70aa96fc1"
#         "8fca376070b84bea4d4c42c736a378de")
