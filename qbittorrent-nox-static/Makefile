#
# Copyright (C) 2017-2020
#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qbittorrent-nox-static
PKG_VERSION:=5.0.4
PKG_RELEASE:=1

PKG_FULL_VERSION:=5.0.4_v2.0.11

STRIP:=true

ifeq ($(ARCH),i386)
	PKG_ARCH:=x86
	PKG_HASH:=81055df070127e294f0d53ec244bdcc6876e023d49ac4a5604a7b6ebe9e47e2a
endif

ifeq ($(ARCH),x86_64)
	PKG_ARCH:=x86_64
	PKG_HASH:=fee4fc740aaebf255804bed12a7925b00afc90c24d7b54fd2079d9b7268e0d9c
endif

ifeq ($(ARCH),aarch64)
	PKG_ARCH:=aarch64
	PKG_HASH:=f4f7f368b6b5a01449c6562ea38cfb73ad48a917d5e0fbd80122aaf8a8213c4c
endif

ifeq ($(ARCH),arm)
	PKG_ARCH:=armv7
	PKG_HASH:=f46973a8e7c0d51f33fe83061cb82bb8488e769e42038a72df0b2451fa249899
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

