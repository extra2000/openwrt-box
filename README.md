# openwrt-box

| License | Versioning | Build |
| ------- | ---------- | ----- |
| [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) | [![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release) | [![Build status](https://ci.appveyor.com/api/projects/status/m5d4el3isqh5enkn/branch/master?svg=true)](https://ci.appveyor.com/project/nikAizuddin/openwrt-box/branch/master) |

Developer box for [OpenWrt](https://github.com/openwrt/openwrt).


## Getting Started

Clone this repository and `cd`:
```
$ git clone --recursive https://github.com/extra2000/openwrt-box.git
$ cd openwrt-box
```

Clone OpenWrt repository:
```
$ git clone https://github.com/openwrt/openwrt.git salt/roots/formulas/openwrt-formula/openwrt/files/openwrt
```


## Creating Vagrant Box

Create pillar file `openwrt.sls` based on `openwrt.sls.example`:
```
$ cp -v salt/roots/pillar/openwrt.sls.example salt/roots/pillar/openwrt.sls
```

Copy vagrant file from `vagrant/examples/` and then create the vagrant box (you can change to `--provider=libvirt` if you want to use Libvirt provider):
```
$ cp -v vagrant/examples/Vagrantfile.openwrt-box.fedora-33.x86_64.example vagrant/Vagrantfile.openwrt-box
$ vagrant up --provider=virtualbox
```

Provision the vagrant box and build OpenWrt firmware builder image:
```
$ vagrant ssh openwrt-box -- sudo salt-call state.highstate
$ vagrant ssh openwrt-box -- sudo salt-call state.sls openwrt
```


## Building OpenWrt Firmware

To change `uci` configurations, change the values in `salt/roots/formulas/openwrt-formula/openwrt/files/openwrt/package/base-files/files/bin/config_generate`. Then, `rsync` to upload changes into the Vagrant box:
```
$ vagrant rsync
```

SSH into the Vagrant box and do the following prerequisite steps:
```
$ vagrant ssh openwrt-box
$ podman run -it --rm -v /opt/openwrt/src:/opt/src:rw,z -u root:root localhost/extra2000/firmwarebuilder bash
# cd /opt/src/
# ./scripts/feeds update -a
# ./scripts/feeds install -a
# FORCE_UNSAFE_CONFIGURE=1 make menuconfig
```

Set the following option during `menuconfig`:
* Target System: `MediaTek Ralink MIPS`
* Subtarget: `MT76X8`
* Target Profile: `Asus RT-N11P B1`

To minimize firmware space and RAM, make sure to set the following configuration while in the `make menuconfig`:
* Base system:
    * [ ] `opkg`
* Network/Firewall:
    * [ ] `ip6tables`
    * [ ] `iptables`
* Network:
    * [ ] `ppp`
        * [ ] `ppp-mod-pppoe`

Build firmware:
```
# FORCE_UNSAFE_CONFIGURE=1 make
```

Output can be found in `/opt/openwrt/src/bin/targets/ramips/mt76x8/`. To download from the Vagrant box to host:
```
$ vagrant scp openwrt-box:/opt/openwrt/src/bin/targets/ramips/mt76x8/openwrt-ramips-mt76x8-asus_rt-n11p-b1-initramfs-kernel.bin .
```
