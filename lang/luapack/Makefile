#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=luapack
PKG_VERSION:=1.0.2
PKG_RELEASE:=1

_BASENAME:=LuaPack

PKG_MAINTAINER:=Luiz Henrique <luiz@google.com>
PKG_SOURCE:=lpack.tar.gz
PKG_SOURCE_URL:=http://webserver2.tecgraf.puc-rio.br/~lhf/ftp/lua/5.1/
PKG_MD5SUM:=e6fe2f72fd6447b8e1712bbb95b32493
PKG_BUILD_DIR:=$(BUILD_DIR)/pack
PKG_LICENSE:=MIT

include $(INCLUDE_DIR)/package.mk

define Package/luapack
  SUBMENU:=Lua
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=luapack
  URL:=http://webserver2.tecgraf.puc-rio.br/~lhf/
  DEPENDS:=+lua
endef

define Package/luapack/description
Lua Pack is a Lua library for packing and unpacking binary data
endef

define Build/Configure
endef


TARGET_CFLAGS += $(FPIC) -DLUA_USE_LINUX -DLUA_NUMBER_DOUBLE

define Build/Compile
	$(TARGET_CC) $(TARGET_CFLAGS) $(TARGET_CPPFLAGS) $(TARGET_CPPFLAGS) -ansi -pedantic -Wall $(FPIC) -DLUA_USE_LINUX -shared -o $(PKG_BUILD_DIR)/pack.so $(PKG_BUILD_DIR)/lpack.c
endef

define Package/luapack/install
	$(INSTALL_DIR) $(1)/usr/lib/lua
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/pack.so $(1)/usr/lib/lua
endef

$(eval $(call BuildPackage,luapack))
