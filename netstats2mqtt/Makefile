# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2026 Bernhard Fröhlich <decke@bluelife.at>

include $(TOPDIR)/rules.mk

PKG_NAME:=netstats2mqtt
PKG_VERSION:=2026.02.17
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeberg.org/decke/netstats2mqtt/archive/v$(PKG_VERSION).tar.gz
PKG_HASH:=c6d6a7921127a3a54fbdcffc2a33145036b56a61f04441c063c0088ab6528860

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Bernhard Fröhlich <decke@bluelife.at>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=codeberg.org/decke/netstats2mqtt

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/netstats2mqtt
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Send interface traffic statistics to MQTT
  URL:=https://codeberg.org/decke/netstats2mqtt
  DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle
endef

define Package/netstats2mqtt/description
  Send interface traffic statistics to MQTT
endef

define Package/netstats2mqtt/conffiles
/etc/config/netstats2mqtt
endef

define Package/netstats2mqtt/install
  $(INSTALL_DIR) $(1)/etc/config
  $(INSTALL_CONF) ./files/netstats2mqtt.config $(1)/etc/config/netstats2mqtt
  $(INSTALL_DIR) $(1)/etc/init.d
  $(INSTALL_BIN) ./files/netstats2mqtt.init $(1)/etc/init.d/netstats2mqtt
#  $(INSTALL_DIR) $(1)/usr/sbin/
#  $(INSTALL_BIN) $(PKG_BUILD_DIR)/netstats2mqtt $(1)/usr/sbin/
endef

$(eval $(call GoBinPackage,netstats2mqtt))
$(eval $(call BuildPackage,netstats2mqtt))
