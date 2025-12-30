# luci-app-clouddrive2

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

- Install `curl` package
  ```shell
  # for opkg package manager (openwrt 21.02 ~ 24.10)
  opkg update
  opkg install curl ca-bundle
  
  # for apk package manager
  apk update
  apk add curl ca-bundle
  ```

- Execute install script (Multi-architecture support)
  ```shell
  sh -c "$(curl -ksS https://raw.githubusercontent.com/xuanranran/openwrt-clouddrive2/main/install.sh)"
  ```

  install via ghproxy:
  ```shell
  sh -c "$(curl -ksS https://gh.cooluc.com/https://raw.githubusercontent.com/xuanranran/openwrt-clouddrive2/main/install.sh)" _ gh_proxy="https://gh.cooluc.com/"
  ```

--------------
