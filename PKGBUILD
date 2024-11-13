# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Kyle Keen <keenerd@gmail.com>
# Contributor: Will Shanks <wsha dot code at g mail dot com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=ptyprocess
_proj="pexpect"
pkgname="${_py}-${_pkg}"
pkgver=0.7.0
pkgrel=6
pkgdesc="Run a subprocess in a pseudo terminal"
_http="https://github.com"
_ns="${_proj}"
url="${_http}/${_ns}/${_pkg}"
arch=(
  'any'
)
license=(
  'ISC'
)
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-wheel"
  "${_py}-flit-core"
)
_pypa="https://pypi.io/packages/source"
_gh_raw="https://raw.githubusercontent.com"
source=(
  "${_pypa}/${_pkg::1}/${_pkg}/${_pkg}-${pkgver}.tar.gz"
  "LIC-pty-${pkgver}::${_gh_raw}/${_ns}/${_pkg}/master/LICENSE"
)
sha512sums=(
  '791d8f2e79900627215ce80ce67ee9c79173dbc08297c6219d5058f9b80c5e323b93049e6836a70c4073f43548d22e3cf310f2e9948ef12f96bcaa15b0ddb2f3'
  '77465d8319848ad6e4c3811276d6f7f5241f715d1f72012f155f5a1850abc6542fe7a74fcafc39d9801def60884d6d1acc4393700a552e44a05b763ae84970f0'
)

prepare() {
  cd \
    "${srcdir}"
  # python2
  # cp \
  #   -r \
  #   "${_pkg}-${pkgver}" \
  #   "${_pkg}2-${pkgver}"
  mv \
    "LIC-pty-${pkgver}" \
    "LICENSE"
}

build() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      build \
    --wheel \
    --no-isolation
}

package() {
  local \
    _opts=()
  _opts=(
    -m
      installer
    --destdir="${pkgdir}"
  )
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  "${_py}" \
    "${_opts[@]}" \
    dist/*.whl
  install \
    -Dm644 \
    "${srcdir}/LICENSE" \
    "${pkgdir}/usr/share/licenses/python-${_pkgname}/LICENSE"
}

