#
# Copyright (C) 2017-2020
#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qbittorrent-nox-static
PKG_VERSION:=5.1.0
PKG_RELEASE:=1

PKG_FULL_VERSION:=5.1.0_v2.0.11

STRIP:=true

ifeq ($(ARCH),i386)
	PKG_ARCH:=x86
	PKG_HASH:=b3a767941464c080d8459b4be824fefadd68f1c0ae64f661db9b8d5cca5055cc
endif

ifeq ($(ARCH),x86_64)
	PKG_ARCH:=x86_64
	PKG_HASH:=5b294474e10ecda07dbf2b67e9b73a7750fb75380b840e35dc0160187fdd7ef9
endif

ifeq ($(ARCH),aarch64)
	PKG_ARCH:=aarch64
	PKG_HASH:=88cb8064aa38f1e102f4020c8d152451c3334e2daac5aa16c127cbc9a24a48f3
endif

ifeq ($(ARCH),arm)
	PKG_ARCH:=armv7
	PKG_HASH:=367e84d33c75b35dcb727101856ccd765e74170bc1308bf78407645b570357cc
endif

include $(INCLUDE_DIR)/package.mk

define Package/qbittorrent-nox-static
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=@(arm||aarch64||i386||x86_64)
	SUBMENU:=BitTorrent
	TITLE:=bittorrent client programmed in C++ / Qt
	URL:=https://github.com/userdocs/qbittorrent-nox-static
	PROVIDES:=qBittorrent
endef

define Package/qbittorrent-nox-static/description
  The qbittorrent-nox-static project is a bash build script that compiles
  a static qbittorrent-nox binary using the latest available dependencies
  from their source. These statically linked binaries can run on any
  matching CPU architecture and are not OS specific.

  See: https://github.com/userdocs/qbittorrent-nox-static
endef

define Download/qbittorrent-nox-static
	URL:=https://github.com/userdocs/qbittorrent-nox-static/releases/download/release-$(PKG_FULL_VERSION)
	URL_FILE:=$(PKG_ARCH)-qbittorrent-nox
	FILE:=qbittorrent-nox-$(PKG_ARCH)-$(PKG_FULL_VERSION)
	HASH:=$(PKG_HASH)
endef

define Package/qbittorrent-nox-static/conffiles
/etc/config/qbittorrent
endef

define Build/Compile
endef

define Package/qbittorrent-nox-static/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(DL_DIR)/qbittorrent-nox-$(PKG_ARCH)-$(PKG_FULL_VERSION) $(1)/usr/bin/qbittorrent-nox

	$(INSTALL_DIR) $(1)/etc/config $(1)/etc/init.d $(1)/usr/share/qbittorrent
	$(INSTALL_BIN) ./files/qbittorrent.init $(1)/etc/init.d/qbittorrent
	$(INSTALL_CONF) ./files/qbittorrent.config $(1)/etc/config/qbittorrent
	$(INSTALL_CONF) ./files/qBittorrent.conf.example $(1)/usr/share/qbittorrent/qBittorrent.conf.example
endef

$(eval $(call Download,qbittorrent-nox-static))
$(eval $(call BuildPackage,qbittorrent-nox-static))

