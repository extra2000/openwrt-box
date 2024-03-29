# Changelog

## [2.1.0](https://github.com/extra2000/openwrt-box/compare/v2.0.2...v2.1.0) (2021-05-02)


### Features

* **vagrant:** Add Fedora 34 `x86_64` Vagrant file ([82fb2b0](https://github.com/extra2000/openwrt-box/commit/82fb2b002e175023b49302b969fd5e11dbf95ad9))
* **vagrant:** Upgrade CentOS Stream from `v20201217.0` to `v20210210.0` ([84caecc](https://github.com/extra2000/openwrt-box/commit/84caeccf35ddd3a6baf8b7e79f7dde87eab8b9f4))
* **vagrant:** Upgrade SaltStack from `v3002.2` to `v3003` ([3f4efba](https://github.com/extra2000/openwrt-box/commit/3f4efbaaeec492de4fe5839c83f36b7970c8f99d))


### Documentations

* **README:** Set Fedora 34 as default Vagrant instruction ([4ab6b4d](https://github.com/extra2000/openwrt-box/commit/4ab6b4dc59f24f99eec96e30a79fc55c43909966))

### [2.0.2](https://github.com/extra2000/openwrt-box/compare/v2.0.1...v2.0.2) (2021-04-06)


### Code Refactoring

* **submodule:** Remove `cockpit-formula` ([2bcc7af](https://github.com/extra2000/openwrt-box/commit/2bcc7af5f634e163ec4d1cd3bfce5122ce7e6d72))


### Fixes

* **submodule:** Update `openwrt-formula` to [v2.0.1](https://github.com/extra2000/openwrt-formula/releases/tag/v2.0.1) which includes python development packages ([3347d8b](https://github.com/extra2000/openwrt-box/commit/3347d8ba9b5348a069ff3dd4d7e7e91a2e200f33))


### Documentations

* **README:** Add instructions to enable FreeRadius for WPA2/WPA3 Enterprise ([7869e69](https://github.com/extra2000/openwrt-box/commit/7869e69241a6efda8dca8f77eabf1f718068d5e8))
* **README:** Add instructions to re-apply `openwrt` state after `vagrant rsync` ([6fc9368](https://github.com/extra2000/openwrt-box/commit/6fc93688537d8c23d8922cdfcc82f5de8342daf7))
* **README:** Change `make` into more verbose ([bf7b832](https://github.com/extra2000/openwrt-box/commit/bf7b8329c55f7c720a282fcbe496ea2f0c9cbfa9))
* **README:** Notes to user that they don't need to update and install `feeds` everytime they enter the `extra2000/firmwarebuilder` container ([60dbff9](https://github.com/extra2000/openwrt-box/commit/60dbff98db3ac1b2ae068467a34baa21755258ec))

### [2.0.1](https://github.com/extra2000/openwrt-box/compare/v2.0.0...v2.0.1) (2021-03-15)


### Documentations

* **README:** Add instructions to minimize firmware size ([91f8227](https://github.com/extra2000/openwrt-box/commit/91f82278abd6f9411cafcca655628657a2479e4e))
* **README:** Improve build instructions ([b2eeb09](https://github.com/extra2000/openwrt-box/commit/b2eeb097e88568ccbc465b74dbb7906c51a0de30))

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
