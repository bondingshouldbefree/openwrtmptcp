# SPDX-License-Identifier: GPL-3.0-only

include $(TOPDIR)/rules.mk

PKG_NAME:=ratbond
PKG_VERSION:=1.0
PKG_RELEASE:=5

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/roelfdiedericks/ratbond.git
PKG_SOURCE_VERSION:=fe41cc25f91d98a8f02d09e5710a2dacafc1b98f
PKG_HASH:=skip

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=github.com/roelfdiedericks/ratbond
GO_PKG_BUILD_PKG:=$(GO_PKG)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/ratbond
  TITLE:=ratbond
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=$(GO_ARCH_DEPENDS)
endef

define Package/ratbond/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/ratbond $(1)/usr/bin/ratbond

	$(INSTALL_DIR) $(1)/etc/config/
	$(INSTALL_CONF) ./files/ratbond.conf $(1)/etc/config/ratbond
	$(INSTALL_DIR) $(1)/etc/init.d/
	$(INSTALL_BIN) ./files/ratbond.init $(1)/etc/init.d/ratbond
endef

$(eval $(call BuildPackage,ratbond))
