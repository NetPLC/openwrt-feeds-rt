#
# Copyright (C) 2022 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=rt-tests

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://git.kernel.org/pub/scm/utils/rt-tests/rt-tests.git
PKG_REV:=0308cf6ed38e9bf055bddc9d64eda263556f415c
PKG_VERSION:=v2.3
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0

PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_SOURCE_SUBDIR).tar.gz
PKG_MIRROR_HASH:=fd4b337a56993eec9a03ad8e7918bccc7691aa8b2e5ab6dd7863350f07503285
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SOURCE_SUBDIR)

PKG_MAINTAINER:=Han Pengfei <pengphei@qq.com>

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

define Package/rt-tests
  SECTION:=realtime
  CATEGORY:=Realtime
  TITLE:=rt-tests
  DEPENDS:=+libnuma
  URL:=https://rt.wiki.kernel.org/index.php/Main_Page
  DEPENDS:=+libnuma
endef


define Package/rt-tests/description
This repository contains some programs that test various rt-linux features.
endef

MAKE_FLAGS += \
	prefix=/usr

define Package/rt-tests/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/cyclicdeadline $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/cyclictest $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/deadline_test $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/hackbench $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/oslat $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/pip_stress $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/pi_stress $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/pmqtest $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/ptsematest $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/queuelat $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/rt-migrate-test $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/signaltest $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/sigwaittest $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/ssdd $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/svsematest $(1)/usr/bin
endef

$(eval $(call BuildPackage,rt-tests))
