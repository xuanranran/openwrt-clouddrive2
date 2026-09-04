# luci-app-clouddrive2

[![GitHub Release](https://badgen.net/github/release/xuanranran/openwrt-clouddrive2/stable)](https://github.com/xuanranran/openwrt-clouddrive2/releases)

🗂️ A powerful cloud storage management tool for OpenWrt.

## How to build

- Install `libfuse` development package (if compiling locally, otherwise SDK handles it).

  - ubuntu/debian:
    ```shell
    sudo apt update
    sudo apt install libfuse-dev
    ```

- Enter in your openwrt dir

- Openwrt official SnapShots or ImmortalWrt

  *1. get luci-app-clouddrive2 code & building*
  ```shell
  git clone https://github.com/xuanranran/openwrt-clouddrive2 package/clouddrive2
  make menuconfig # choose LUCI -> Applications -> luci-app-clouddrive2
  make package/clouddrive2/luci-app-clouddrive2/compile V=s # build luci-app-clouddrive2
  ```

--------------

## How to install prebuilt packages (LuCI2)

- Login OpenWrt terminal (SSH)

- Install Dependencies / 安装依赖
  ```shell
  # for opkg package manager (openwrt 21.02 ~ 24.10)
  opkg update
  opkg install fuse-utils ca-bundle curl tar
  
  # for apk package manager
  apk update
  apk add fuse-utils ca-bundle curl tar
  ```

- Execute install script (Multi-architecture support)
  ```shell
  sh -c "$(curl -ksS https://raw.githubusercontent.com/xuanranran/openwrt-clouddrive2/master/install.sh)"
  ```

  install via ghproxy:
  ```shell
  sh -c "$(curl -ksS https://ghproxy.net/https://raw.githubusercontent.com/xuanranran/openwrt-clouddrive2/master/install.sh)" _ gh_proxy="https://ghproxy.net/"
  ```

## Configuration persistence

CloudDrive2 stores its runtime configuration in `/etc/CloudDrive2`. Existing
installations are migrated automatically from `/etc/Waytech/CloudDrive2` or
`/Waytech/CloudDrive2` on the next service start. The package also adds this
directory to OpenWrt's sysupgrade keep list so it is included when firmware
settings are preserved.

The HTTP/HTTPS ports and cloud mount points are managed in CloudDrive2's own
web interface. This package runs the native CloudDrive2 binary rather than a
Docker container. Mounting cloud drives under `/mnt` is recommended and works
especially well with the Samba4 package. The LuCI page only enables or disables
the service. Before startup, the init script reads the configured `http_port`
from `/etc/CloudDrive2/config.toml` (defaulting to `19798`) and refuses to start
if another process is already listening on that port.

--------------
