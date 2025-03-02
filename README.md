# luci-app-qbittorrent-static

## Summary
The `luci-app-qbittorrent-static` project is a qBittorrent client for OpenWrt, utilizing the static binary from the `qbittorrent-nox-static` project. This project will update its qBittorrent version in sync with the qbittorrent-nox-static project.

>The `qbittorrent-nox-static` project is a bash build script that compiles a static qbittorrent-nox binary using the latest available dependencies from their source. These statically linked binaries can run on any matching CPU architecture and are not OS specific.

See: [qbittorrent-nox-static](https://github.com/userdocs/qbittorrent-nox-static)

## Support Target
Due to the use of a static binary from the qbittorrent-nox-static project, this project only supports **the following targets**:
```
arm
aarch64
i386
x86_64
```

## About Default Password
The WebUI administrator username is: **admin**

The WebUI administrator password is: **adminamdin**

You should **set your own password** in program preferences.

## How to build
Navigate to openwrt/package/ or another appropriate directory, then run the following commands to install luci-app-qbittorrent-static on OpenWrt:

``` bash
git clone https://github.com/teleostnacl/luci-app-qbittorrent-static.git
make menuconfig  # Select LUCI -> Applications -> luci-app-qbittorrent-static
make V=s
```
