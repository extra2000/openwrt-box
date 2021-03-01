# Changelog

## [2.0.0](https://github.com/extra2000/openwrt-box/compare/v1.0.0...v2.0.0) (2021-03-01)


### ⚠ BREAKING CHANGES

* **openwrt-formula:** Require `git clone` OpenWrt repository into `salt/roots/formulas/openwrt-formula/openwrt/files/openwrt`

### Documentations

* **README:** Add instruction to clone OpenWrt repo ([d8997ea](https://github.com/extra2000/openwrt-box/commit/d8997ea544f21dbb9f18604fa3c8ea40ecbcf86e))


### Fixes

* **openwrt-formula:** Update `openwrt-formula` to [v2.0.0](https://github.com/extra2000/openwrt-formula/releases/tag/v2.0.0) which remove OpenWrt from `git submodule` ([b0cad59](https://github.com/extra2000/openwrt-box/commit/b0cad5982fbf28eb0461f8288aec36d9cbb52fcb))


### Continuous Integrations

* **AppVeyor:** Add instruction to clone OpenWrt repo ([bd4fb40](https://github.com/extra2000/openwrt-box/commit/bd4fb4023b7083648a40ac7116e69e388f509945))

## 1.0.0 (2021-02-17)


### Features

* **salt:** Add implementations for SaltStack states in `salt/` ([7c57491](https://github.com/extra2000/openwrt-box/commit/7c574914711a20100e12c7139b95278247577bae))
* **submodule:** Add [cockpit-formula v1.0.3](https://github.com/extra2000/cockpit-formula/releases/tag/v1.0.3) ([69689c6](https://github.com/extra2000/openwrt-box/commit/69689c6be572f38bf0fd936fd22faa4561160961))
* **submodule:** Add [openwrt-formula v1.0.0](https://github.com/extra2000/openwrt-formula/releases/tag/v1.0.0) ([5972039](https://github.com/extra2000/openwrt-box/commit/5972039588a079a9b3b134a6aac1f70330ef6220))
* **submodule:** Add [podman-formula v2.2.1](https://github.com/extra2000/podman-formula/releases/tag/v2.2.1) ([ef411ff](https://github.com/extra2000/openwrt-box/commit/ef411ff14f2ebe9cb5680ec58e25aa64ab309080))
* **vagrant:** Import Vagrant files from [extra2000/generic-box v1.5.0](https://github.com/extra2000/generic-box/releases/tag/v1.5.0) ([954c568](https://github.com/extra2000/openwrt-box/commit/954c568d09a2b315a3f1f165cfeeecc145355d0a))


### Continuous Integrations

* Add AppVeyor and `semantic-release` bot ([5007847](https://github.com/extra2000/openwrt-box/commit/5007847e85ecdf4f734da80fa3ca7a3769d49ab9))


### Documentations

* **README:** Update `README.md` ([403fafe](https://github.com/extra2000/openwrt-box/commit/403fafe0e4655d319a0ee4d7309d916836b7b0dd))
