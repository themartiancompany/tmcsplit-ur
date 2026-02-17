# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025, 2026  Pellegrino Prevete
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
  _npm="false"
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
_pkg=opfs
pkgbase="${_node}-${_pkg}"
pkgname=(
  "${pkgbase}"
)
_pkgdesc=(
  "Browser-compatible 'fs' module"
  "obtained combining the"
  "'Happy OPFS' and the"
  "OPFS Tools modules."
)
pkgdesc="${_pkgdesc[*]}"
_commit="8560a11f42a0e0208e7e915daca6b811dfea860d"
pkgver="2.0.5"
pkgrel=1
arch=(
  'any'
)
_http="https://${_git_http}.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${_pkg}"
license=(
  'AGPL3'
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
if [[ "${_npm}" == "true" ]]; then
  _tag="${pkgver}"
  _tag_name="pkgver"
elif [[ "${_npm}" == "false" ]]; then
  _tag="${_commit}"
  _tag_name="commit"
fi
_tarname="${_pkg}-${_tag}"
_npm_tarname="${_ns}-${_pkg}-${_tag}"
_tarfile="${_tarname}.${_archive_format}"
_npm_tarfile="${_npm_tarname}.${_archive_format}"
_sum="c260bc56e3eb822f96ea10bdef55b4158a7cc5b4ec55503f61f1cdff367e407a"
_sig_sum="bca05e0d77e803cbfbf8304192b62964159fe71e6bcb8023bcae5954eab6258a"
_bundle_sum="e7bf622ac1afab6ebdd14f6ff621874d24aca9e4899f1fa7616a84faea4ed81c"
_bundle_sig_sum="bdf198594304ccfd8d262ffa4ff5f1a0511ee198a73b1c74ed227f346eda4998"
_npm_sum="e6f8f5b672465be2bfac83de21f575578612afe510b8fc059e1ce839c4cdc021"
_npm_sig_sum="39f80370d9cf9b32cb9a41b9976ad9a8915ba7c4350ba24b7729b39af6ba3d39"
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
# Truocolo
_evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_bundle_uri="${_evmfs_dir}/${_bundle_sum}"
_bundle_src="${_tarfile}::${_bundle_uri}"
_evmfs_npm_uri="${_evmfs_dir}/${_npm_sum}"
_evmfs_npm_src="${_tarfile}::${_evmfs_npm_uri}"
_evmfs_sig_uri="${_evmfs_dir}/${_sig_sum}"
_evmfs_sig_src="${_tarfile}.sig::${_evmfs_sig_uri}"
_bundle_sig_uri="${_evmfs_dir}/${_bundle_sig_sum}"
_bundle_sig_src="${_tarfile}.sig::${_bundle_sig_uri}"
_npm_sig_uri="${_evmfs_dir}/${_npm_sig_sum}"
_npm_sig_src="${_tarfile}.sig::${_npm_sig_uri}"
_npm_http="http://registry.npmjs.org"
source=()
sha256sums=()
if [[ "${_evmfs}" == "true" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_evmfs_npm_uri}"
    _sum="${_evmfs_npm_sum}"
    _sig_src="${_evmfs_npm_uri}"
    _sig_sum="${_npm_sig_sum}"
  elif [[ "${_npm}" == "false" ]]; then
    if [[ "${_git}" == "true" ]]; then
      _uri="${_bundle_uri}"
      _sum="${_bundle_sum}"
      _sig_src="${_bundle_sig_src}"
      _sig_sum="${_bundle_sig_sum}"
    elif [[ "${_git}" == "false" ]]; then
      _uri="${_evmfs_uri}"
      _sig_src="${_evmfs_sig_src}"
    fi
  fi
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_npm_http}/@${_ns}/${_pkg}/-/${_tarfile}"
  elif [[ "${_npm}" == "false" ]]; then
    if [[ "${_tag_name}" == 'pkgver' ]]; then
      if [[ "${_git_http}" == "gitlab" ]]; then
        _uri="${url}/archive/refs/tags/${_tag}.${_archive_format}"
      fi
    elif [[ "${_tag_name}" == "commit" ]]; then
      if [[ "${_git_http}" == "github" ]]; then
        _uri="${url}/archive/${_commit}.${_archive_format}"
      elif [[ "${_git_http}" == "gitlab" ]]; then
        _uri="${url}/-/archive/${_commit}/${_tarname}.${_archive_format}"
      fi
    fi
  fi
fi
if [[ "${_npm}" == "true" ]]; then
  _tarfile="${_npm_tarfile}"
fi
_src="${_tarfile}::${_uri}"
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)
if [[ "${_npm}" == "true" ]]; then
  noextract=(
    "${_tarfile}"
  )
fi
validpgpkeys=(
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
  #   <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
)

package_nodejs-opfs() {
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
26d4230e0bff3acbd8618eb34aeb93f08a94281e9ac0c54f3f8758ad5225d2d1  opfs-8560a11f42a0e0208e7e915daca6b811dfea860d.zip
296c4fb420c0275d01d095ea9cbcb49ecb25791346d26699c512c073634f6ebb  /home/dev/opfs-8560a11f42a0e0208e7e915daca6b811dfea860d.zip.sig
