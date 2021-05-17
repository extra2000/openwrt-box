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

Create pillar files:
```
$ cp -v salt/roots/pillar/podman.sls.example salt/roots/pillar/podman.sls
$ cp -v salt/roots/pillar/openwrt.sls.example salt/roots/pillar/openwrt.sls
```

Copy vagrant file from `vagrant/examples/` and then create the vagrant box (you can change to `--provider=libvirt` if you want to use Libvirt provider):
```
$ cp -v vagrant/examples/Vagrantfile.openwrt-box.fedora-34.x86_64.example vagrant/Vagrantfile.openwrt-box
$ vagrant up --provider=virtualbox
```

Provision the vagrant box and build OpenWrt firmware builder image:
```
$ vagrant ssh openwrt-box -- sudo salt-call state.highstate
$ vagrant ssh openwrt-box -- sudo salt-call state.sls openwrt
```


## Building OpenWrt Firmware

To change `uci` configurations, change the values in `salt/roots/formulas/openwrt-formula/openwrt/files/openwrt/package/base-files/files/bin/config_generate`. Then, `rsync` to upload changes into the Vagrant box and re-apply `openwrt` state:
```
$ vagrant rsync
$ vagrant ssh openwrt-box -- sudo salt-call state.sls openwrt
```

SSH into the Vagrant box and then run `extra2000/firmwarebuilder` Podman container:
```
$ vagrant ssh openwrt-box
$ podman run -it --rm -v /opt/openwrt/src:/opt/src:rw,z -u root:root localhost/extra2000/firmwarebuilder bash
# cd /opt/src/
```

Update and install all feeds. Note that these steps are required for the fresh OpenWrt repository only. You don't need to re-execute these steps everytime you run the `extra2000/firmwarebuilder` Podman container:
```
# ./scripts/feeds update -a
# ./scripts/feeds install -a
```

Configure build:
```
# FORCE_UNSAFE_CONFIGURE=1 make menuconfig
```

Set the following option during `menuconfig`:
* Target System: `MediaTek Ralink MIPS`
* Subtarget: `MT76X8`
* Target Profile: `Asus RT-N11P B1`

To minimize firmware space and RAM, make sure to set the following configuration while in the `make menuconfig`:
* Base system:
    * `< >` `opkg`
    * `<*>` `zram-swap`
* Network:
    * `< >` `ppp`
        * `< >` `ppp-mod-pppoe`

To build with Zabbix agent:
* Administration > Zabbix:
    * `<*>` `zabbix-agentd`
    * `<*>` `zabbix-extra-mac80211`
    * `<*>` `zabbix-extra-network`
    * `<*>` `zabbix-extra-wifi`

To build with FreeRadius for WPA3 Enterprise:
* Network > FreeRADIUS (version 3):
    * `<*>` `freeradius3`
    * `<*>` `freeradius3-common`
    * `<*>` `freeradius3-default`
    * `<*>` `freeradius3-utils`
* Network > WirelessAPD:
    * `<*>` `wpad`

To find out what parameters have been set by the `make menuconfig`, execute the following command:
```
# grep -v "^\s*$\|^\s*\#" .config | less
```

Build firmware:
```
# FORCE_UNSAFE_CONFIGURE=1 make clean
# FORCE_UNSAFE_CONFIGURE=1 make download
# FORCE_UNSAFE_CONFIGURE=1 make -j1 V=s
```

Output can be found in `/opt/openwrt/src/bin/`. To download from the Vagrant box to host:
```
$ vagrant scp openwrt-box:/opt/openwrt/src/bin .
```


## Configure FreeRadius for WPA3 Enterprise

See https://openwrt.org/docs/guide-user/network/wifi/freeradius#configuration
