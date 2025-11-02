# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.


# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_os="$( \
  uname \
    -o)"
_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
_node="nodejs"
if [[ "${_os}" == "Android" ]]; then
  _node="nodejs-lts"
fi
if [[ ! -v "_npm" ]]; then
  _npm="true"
fi
if [[ ! -v "_git_http" ]]; then
  _git_http="github"
fi
_archive_format="tgz"
if [[ ! -v "${_archive_format}" ]]; then
  if [[ "${_npm}" == "false" ]]; then
    if [[ "${_git_http}" == "github" ]]; then
      _archive_format="zip"
    fi
  fi
fi
_pkg=rollup
pkgbase="${_node}-${_pkg}"
pkgname=(
  "${pkgbase}"
)
_pkgdesc=(
  "Browser-compatible fs module"
  "based on OPFS, which references"
  "the Deno Runtime File System"
  "and Deno @std/fs APIs."
)
pkgdesc="${_pkgdesc[*]}"
pkgver=4.52.5
_commit="17bbfff4add818aa762a9bfceca10d29143e2fb8"
pkgrel=1
arch=(
  'any'
)
_http="https://${_git_http}.com"
_ns="JiangJie"
url="${_http}/${_ns}/${_pkg}"
license=(
  'MIT'
)
depends=(
  "${_node}"
)
provides=(
  "${_pkg}=${pkgver}"
)
makedepends=(
  "npm"
)
_tarname="${_pkg}-${pkgver}"
_tarfile="${_tarname}.${_archive_format}"
_sum="d49906ca8f1488dc73fb20e692523cbd1f778caaecefeb368166e0fb6d9d78ef"
_sig_sum="6122a66cdcdbfe0c58c0744db63d3ce9cebcf2c12080a5765f149b964807d8a0"
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
# Truocolo
_evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_sig_uri="${_evmfs_dir}/${_sig_sum}"
_sig_src="${_tarfile}.sig::${_sig_uri}"
_npm_http="http://registry.npmjs.org"
source=()
sha256sums=()
if [[ "${_evmfs}" == "true" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_evmfs_uri}"
    source+=(
      "${_sig_src}"
    )
    sha256sums+=(
      "${_sig_sum}"
    )
  fi
elif [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_npm_http}/${_pkg}/-/${_tarfile}"
  fi
fi
_src="${_tarfile}::${_uri}"
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)
noextract=(
  "${_tarfile}"
)

package_nodejs-rollup() {
  local \
    _npm_options=() \
    _find_opts=()
  _npm_options=(
    -g 
    # --user 
    #   root 
    --prefix 
      "${pkgdir}/usr"
  )
  find_opts+=(
    -type
      "d"
    -exec
      chmod
        755
        '{}'
        +
  )
  npm \
    install \
    "${_npm_options[@]}" \
    "${srcdir}/${_pkg}-${pkgver}.tgz"
  rm \
    -fr \
      "${pkgdir}/usr/etc"
  # Fix npm derp
  find \
    "${pkgdir}/usr" \
    "${_find_opts[@]}"
}

# vim:set sw=2 sts=-1 et:
