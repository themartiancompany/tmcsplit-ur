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

_os="$(
  uname \
    -o)"
_evmfs_available="$(
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
  # This will have to be removed when we
  # will have non-termux missing-provides bugged
  # life and dogeos android nodejs and nodejs-lts
  # builds.
  _node_lts="$(
    ( pacman \
       -Q \
       "nodejs-lts" \
       2>"/dev/null" || \
      pacman \
        -Q \
        "nodejs" ) | \
      awk \
        '{print $1}' \
      2>/dev/null)"
  if [[ "${_node_lts}" != "" ]]; then
    _node="nodejs-lts"
  fi
fi
if [[ ! -v "_npm" ]]; then
  _npm="false"
fi
if [[ ! -v "_make" ]]; then
  _make="true"
fi
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_git_http" ]]; then
  _git_http="github"
fi
_archive_format="tgz"
if [[ ! -v "${_archive_format}" ]]; then
  if [[ "${_npm}" == "false" ]]; then
    if [[ "${_git_http}" == "github" ]]; then
      _archive_format="zip"
    elif [[ "${_git_http}" == "gitlab" ]]; then
      _archive_format="tar.xz"
    fi
  fi
fi
_Pkg=split
_pkg=tmc${_Pkg}
pkgbase="${_pkg}"
pkgname=(
  "${pkgbase}"
)
_pkgdesc=(
  "Javascript GNU Split rewrite."
)
pkgdesc="${_pkgdesc[*]}"
_commit="93cc4e1ed829411d01c4e4df74339e4b958b667c"
_pkgver="0.0.19"
pkgver="0.0.19"
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
  "${_node}-${_pkg}=${pkgver}"
)
makedepends=(
)
if [[ "${_make}" == "true" ]]; then
  makedepends+=(
    "make"
  )
fi
if [[ "${_npm}" == "true" ]]; then
  makedepends+=(
    "npm"
  )
fi
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
_sum="fbc07261ffcca082270f9f500f4790fd6c36872701306d805b145a2c5a7edb92"
_sig_sum="abb8f1bfe47679ee5965138b4f946d1faabbc60dfc9a83ff7e0ea5aac7b84ab9"
_bundle_sum="SKIP"
_bundle_sig_sum="SKIP"
_npm_sum="955bf6257050df3240b3e4a9575c31a6485325dd9be2e56613f4ada51f851634"
_npm_sig_sum="c123a0ee31890699dbbae4da5902ebd1aed9c0f890635ffe2438de9f12f9f146"
# Truocolo
_evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
# Gnosis
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
    _uri="${_npm_http}/${_pkg}/-/${_tarfile}"
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

build() {
  local \
    _files=()
  if [[ "${_make}" == "false" && \
        "${_npm}" == "false" ]]; then
    _files+=(
      "AUTHORS.rst"
      "COPYING"
      "README.md"
      "eslint.config.mjs"
      "fs-worker.webpack.config.cjs"
      "lib${_pkg}"
      "index.html"
      "man"
      "package.json"
      "serve.json"
      "${_pkg}"
      "webpack.config.cjs"
    )
    cd \
      "${_tarname}"
    mkdir \
      -p \
      "build"
    cp \
      -r \
      "${_files[@]}" \
      "build"
    cd \
      "build"
    npm \
      install
    npm \
      pack
    mv \
      "${_ns}-${_Pkg}-${_pkgver}.tgz" \
      "${srcdir}"
  fi
}

package_tmcsplit() {
  local \
    _npm_options=() \
    _find_opts=()
  if [[ "${_make}" == "true" ]]; then
    _make_opts+=(
      DESTDIR="${pkgdir}"
    )
    make \ 
      "${_make_opts[@]}" \
      install-scripts
  fi
  if [[ "${_npm}" == "true" ]]; then
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
      "${srcdir}/${_ns}-${_Pkg}-${_pkgver}.tgz"
    rm \
      -fr \
        "${pkgdir}/usr/etc"
    # Fix npm derp
    find \
      "${pkgdir}/usr" \
      "${_find_opts[@]}"
  fi
}

# vim:set sw=2 sts=-1 et:
