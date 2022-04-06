#
# Copyright (C) 2022 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=preempt-test

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/ghaskins/preempt-test.git
PKG_REV:=e6c9820879929f67df9c32d7b5088956e703e487
PKG_VERSION:=1.0
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

MAKE_FLAGS += \
	prefix=/usr

define Package/preempt-test
  SECTION:=realtime
  CATEGORY:=Realtime
  TITLE:=preempt-test
  DEPENDS:=+boost +boost-system +boost-thread +boost-program_options
  URL:=https://rt.wiki.kernel.org/index.php/Main_Page
endef

define Package/preempt-test/description
This will test several attributes of the linux RT scheduler.  It checks to
make sure that the scheduler allows higher priority tasks to preempt lower
ones, and it measures the latency it takes to do so.
endef

define Package/preempt-test/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/preempt-test $(1)/usr/bin
endef

$(eval $(call BuildPackage,preempt-test))
