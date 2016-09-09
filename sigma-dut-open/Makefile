include $(TOPDIR)/rules.mk

PKG_NAME:=sigma_dut_open
PKG_VERSION:=20160902
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/qca/sigma-dut.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION=0dd682a8c01c4b4be0f1cd0321a3ae94646121a2
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

WIFI_ath9k:=PACKAGE_kmod-ath9k
WIFI_ath10k:=PACKAGE_kmod-ath10k
WIFI_OPEN:=$(WIFI_ath9k)||$(WIFI_ath10k)

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libpthread @$(WIFI_OPEN)
  TITLE:=Sigma DUT
endef

define Package/$(PKG_NAME)/description
  $(PKG_NAME) is a control agent for automating Wi-Fi Alliance certification tests
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/sbin $(1)/etc/init.d $(1)/etc/config
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/sigma_dut $(1)/usr/sbin
	$(INSTALL_BIN) ./files/sigma_dut.init $(1)/etc/init.d/sigma-dut
	$(INSTALL_BIN) ./files/sigma-dut.config $(1)/etc/config/sigma-dut
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
