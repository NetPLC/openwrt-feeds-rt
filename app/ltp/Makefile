#
# Copyright (C) 2022 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ltp

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/linux-test-project/ltp.git
PKG_REV:=91fd818dbff1aa3bcefae3747f83e1dd5c1586dd
PKG_VERSION:=20220121
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0

PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_SOURCE_SUBDIR).tar.gz
PKG_MIRROR_HASH:=fd4b337a56993eec9a03ad8e7918bccc7691aa8b2e5ab6dd7863350f07503285
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SOURCE_SUBDIR)

PKG_MAINTAINER:=Han Pengfei <pengphei@qq.com>

PKG_FIXUP:=libtool autoreconf

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

CONFIGURE_ARGS+= \
	--disable-metadata

define Package/ltp/Default
  SECTION:=realtime
  CATEGORY:=Realtime
  TITLE:=ltp
  URL:=https://wiki.linuxfoundation.org/realtime/documentation/howto/tools/ltp
endef

define Package/ltp-realtime
  $(call Package/ltp/Default)
  TITLE+=(realtime)
endef

MAKE_FLAGS += \
	prefix=/usr

define Package/ltp-realtime/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/hrtimer-prio $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/gtod_latency $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/prio-wake $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/thread_clock $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/pi-tests $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/prio-preempt $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/periodic_cpu_load $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/rt-migrate $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/matrix_mult $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/async_handler $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/sched_footlball $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/pthread_kill_latency $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/measurement $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/sched_latency $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/pi_perf $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/sched_jitter $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/latency $(1)/usr/bin
endef

$(eval $(call BuildPackage,ltp-realtime))
