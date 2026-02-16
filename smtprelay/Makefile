# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2026 Bernhard Fröhlich <decke@bluelife.at>

include $(TOPDIR)/rules.mk

PKG_NAME:=smtprelay
PKG_VERSION:=1.13.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/decke/smtprelay/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=e1256d2a0eaf06331b307e41a902d5f22eb99f6d40966c4e0ece4545a5314490

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Bernhard Fröhlich <decke@bluelife.at>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=github.com/decke/smtprelay

include $(INCLUDE_DIR)/package.mk
include ../feeds/packages/lang/golang/golang-package.mk

define Package/smtprelay
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Simple SMTP relay/proxy server
  URL:=https://github.com/decke/smtprelay
  DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle
endef

define Package/smtprelay/description
  Simple Golang based SMTP relay/proxy server
endef

$(eval $(call GoBinPackage,smtprelay))
$(eval $(call BuildPackage,smtprelay))
