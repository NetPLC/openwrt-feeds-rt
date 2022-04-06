#
# Copyright (C) 2022 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=numactl

PKG_VERSION:=2.0.14
PKG_RELEASE:=1
PKG_REV:=dd6de072c92c892a86e18c0fd0dfa1ba57a9a05d
PKG_MAINTAINER:=Han Pengfei <pengphei@qq.com>

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_MIRROR_HASH:=1051d09069009ad895e6f0af93516301b327a2c3f013f0aaf78d1d416231bd09
PKG_SOURCE_URL:=https://github.com/numactl/$(PKG_NAME).git
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git

PKG_FIXUP:=libtool autoreconf

PKG_MAINTAINER:=Han Pengfei <pengphei@qq.com>

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

define Package/numactl
  SECTION:=realtime
  CATEGORY:=Realtime
  TITLE:=numactl
  DEPENDS:=+libnuma
  URL:=https://github.com/numactl/
endef

define Package/libnuma
  SECTION:=realtime
  CATEGORY:=Realtime
  TITLE:=libnuma
  URL:=https://github.com/numactl/
endef

define Package/numactl-tests
  SECTION:=realtime
  CATEGORY:=Realtime
  TITLE:=numactl-tests
  DEPENDS:=+libnuma
  URL:=https://github.com/numactl/
endef

define Package/numactl/description
simple NUMA policy support.
endef

define Package/libnuma/description
a libnuma shared library ("NUMA API") to set NUMA policy in applications.
endef

define Package/numactl-tests/description
various test and utility programs for NUMA.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libnuma.{la,so*} $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/numa*.pc $(1)/usr/lib/pkgconfig/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
endef

define Package/numactl/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/numactl $(1)/usr/bin/
endef

define Package/numactl-tests/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/memhog $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/migratepages $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/migspeed $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/numademo $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/numastat $(1)/usr/bin/
endef

define Package/libnuma/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libnuma.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,numactl))
$(eval $(call BuildPackage,numactl-tests))
$(eval $(call BuildPackage,libnuma))
