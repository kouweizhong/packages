#
# Copyright (C) 2006-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=irssi
PKG_VERSION:=1.0.5
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://github.com/irssi/irssi/releases/download/1.0.5/
PKG_HASH:=c2556427e12eb06cabfed40839ac6f57eb8b1aa6365fab6dfcd331b7a04bb914

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/irssi
  SUBMENU:=Instant Messaging
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+glib2 +libncurses +libpthread +libopenssl
  TITLE:=Console IRC client
  MAINTAINER:=Peter Wagner <tripolar@gmx.at>
  URL:=https://irssi.org/
endef

define Package/irssi/description
	Irssi is a terminal based IRC client for UNIX systems.
endef

CONFIGURE_ARGS += \
	--with-perl=no \
	--with-glib-prefix="$(STAGING_DIR)/usr" \
	--with-ssl="$(STAGING_DIR)/usr" \
	--with-textui \
	--without-bot \
	--disable-proxy

EXTRA_CFLAGS+=$(TARGET_CPPFLAGS)
EXTRA_LDFLAGS+=-lncurses

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/irssi
	$(CP) $(PKG_INSTALL_DIR)/usr/include/irssi/* $(1)/usr/include/irssi/
endef

define Package/irssi/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/$(PKG_NAME) $(1)/usr/bin/$(PKG_NAME)
endef

$(eval $(call BuildPackage,irssi))

