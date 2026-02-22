# SPDX-License-Identifier: AGPL-3.0


#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025, 2026  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as
#    published by the Free Software Foundation, either version 3 of the
#    License, or (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public
#    License along with this program.
#    If not, see <https://www.gnu.org/licenses/>.

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
    "evmfs" ||
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
if [[ ! -v "_git_http" ]]; then
  _git_http="gitlab"
fi
if [[ ! -v "_archive_format" ]]; then
  if [[ "${_git_http}" == "github" ]]; then
    _archive_format="zip"
  elif [[ "${_git_http}" == "gitlab" ]]; then
    _archive_format="tar.gz"
  fi
fi
if [[ ! -v "_offline" ]]; then
  _offline="false"
fi
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_docs" ]]; then
  _docs="true"
fi
if [[ ! -v "_contracts" ]]; then
  _contracts="true"
fi
if [[ ! -v "_hardhat" ]]; then
  _hardhat="true"
fi
if [[ ! -v "_solc" ]]; then
  _solc="true"
fi
_py="python"
_proj="hip"
_pkg=evm-openpgp-keyserver
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
if [[ "${_contracts}" == "true" ]]; then
  pkgname+=(
    "${_pkg}-contracts"
  )
fi
if [[ "${_docs}" == "true" ]]; then
  pkgname+=(
    "${_pkg}-docs"
  )
fi
pkgver="0.0.0.0.0.0.0.0.0.0.1"
_commit="88cb881bb487beb95385197609e13ba9089cef75"
pkgrel=51
_pkgdesc=(
  "Ethereum Virtual Machine OpenPGP Key Server."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgname}"
license=(
  'AGPL3'
)
depends=(
  "evm-chains-explorers"
  "evm-chains-info"
  "evm-contracts-tools"
  "evm-wallet"
  "evmfs"
  "gnupg"
  "gpg-key-info"
  "libcrash-bash"
)
if [[ "${_os}" != "GNU/Linux" ]] && \
   [[ "${_os}" == "Android" ]]; then
  depends+=(
  )
fi
_evm_gnupg_optdepends=(
  "evm-gnupg:"
    "Reference implementation"
    "of the 'OpenPGP on Ethereum'"
    "specification."
)
_evm_openpgp_keyserver_docs_optdepends=(
  "${_pkg}-docs:"
    "EVM OpenPGP Key Server documentation"
    "and manuals."
)
_evm_openpgp_keyserver_contracts_ref_optdepends=(
   "${_pkg}:"
     "reference EVM OpenPGP Key Server implementation."
)
_evm_openpgp_keyserver_docs_ref_optdepends+=(
 "${_pkg}:"
   "the package this documentation"
   "package pertains to."
)
optdepends=(
  "${_evm_gnupg_optdepends[*]}"
  "${_evm_openpgp_keyserver_docs_optdepends[*]}"
)
makedepends=(
  "binutils"
  'make'
  'solidity-compiler'
)
if [[ "${_docs}" == "true" ]]; then
  makedepends+=(
    "${_py}-docutils"
  )
fi
if [[ "${_contracts}" == "true" ]]; then
  makedepends+=(
    'evm-make'
  )
  if [[ "${_solc}" == "true" ]]; then
    makedepends+=(
      "solidity=0.8.28"
    )
  fi
  if [[ "${_hardhat}" == "true" ]]; then
    makedepends+=(
      "hardhat"
    )
  fi
fi
checkdepends=(
  "shellcheck"
)
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
_tarfile="${_tarname}.${_archive_format}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
_sum="334dbb6bf449a248d1e72ab5a82b1f693fabdd4fdbeca385eef21bea02235633"
_sig_sum="fd49c865d9b7c1c8292d492e660936c8810521bbfd23708bc478e9bfc11172cf"
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_sig_uri="${_evmfs_ns}/${_sig_sum}"
_sig_src="${_tarfile}.sig::${_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
  _src="${_evmfs_src}"
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_git}" == true ]]; then
    makedepends+=(
      "git"
    )
    _src="${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
    _sum="SKIP"
  elif [[ "${_git}" == false ]]; then
    _uri=""
    if [[ "${_git_http}" == "github" ]]; then
      if [[ "${_tag_name}" == "commit" ]]; then
        _uri="${_url}/archive/${_commit}.${_archive_format}"
        _sum="${_github_sum}"
      fi
    elif [[ "${_git_http}" == "gitlab" ]]; then
      if [[ "${_tag_name}" == 'pkgver' ]]; then
        _uri="${_url}/archive/refs/tags/${_tag}.${_archive_format}"
      elif [[ "${_tag_name}" == "commit" ]]; then
        _uri="${_url}/-/archive/${_tag}/${_tag}.${_archive_format}"
      fi
    fi
    _src="${_tarfile}::${_uri}"
  fi
fi
source=(
  "${_src}"
  "COPYING"
)
sha256sums=(
  "${_sum}"
  "0d96a4ff68ad6d4b6f1f30f713b18d5184912ba8dd389f86aa7710db079abcb0"
)
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

check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

build() {
  cd \
    "${_tarname}"
  if [[ "${_solc}" == "true" ]]; then
    SOLIDITY_COMPILER_BACKEND="solc" \
    make \
      all
  fi
  if [[ "${_hardhat}" == "true" ]]; then
    SOLIDITY_COMPILER_BACKEND="hardhat" \
    make \
     all
  fi
}

package_evm-openpgp-keyserver-contracts() {
  local \
    _make_opts=()
  depends=()
  optdepends=(
    "${_evm_openpgp_keyserver_contracts_ref_optdepends[*]}"
  )
  _make_opts=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-contracts-sources
  make \
    "${_make_opts[@]}" \
    install-contracts-deployments-config
  if [[ "${_solc}" == "true" ]]; then
    make \
      "${_make_opts[@]}" \
      install-contracts-deployments-solc
  fi
  if [[ "${_hardhat}" == "true" ]]; then
    make \
      "${_make_opts[@]}" \
      install-contracts-deployments-hardhat
  fi
  install \
    -vDm644 \
    "${srcdir}/COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

package_evm-openpgp-keyserver() {
  local \
    _make_opts=()
  depends+=(
    "${_pkg}-contracts"
  )
  _make_opts=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-scripts
  install \
    -vDm644 \
    "${srcdir}/COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

package_evm-openpgp-keyserver-docs() {
  local \
    _make_opts=()
  depends=()
  optdepends=(
    "${_evm_openpgp_keyserver_docs_ref_optdepends[*]}"
  )
  _make_opts=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-doc \
    install-man
  install \
    -vDm644 \
    "${srcdir}/COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

# vim: ft=2 syn=sh et
