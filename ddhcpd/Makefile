include $(TOPDIR)/rules.mk

PKG_NAME:=ddhcpd
PKG_VERSION:=2019-01-07
PKG_RELEASE:=4

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/sargon/ddhcpd
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=5a5543d72e73a4694a1359f7b7cd84d9b7ae5323
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1

TARGET_CFLAGS += -DLOG_LEVEL=20

include $(TOPDIR)/../package/gluon.mk

define Package/ddhcpd
	SECTION:=net
	CATEGORY:=Network
	TITLE:=ddhcpd
endef

define Package/ddhcpd/description
	distributed dhcp server
endef

define Build/Compile
	$(call Gluon/Build/Compile)
	CFLAGS="$(TARGET_CFLAGS)" BUILD_DIR="$(BUILD_DIR)" $(MAKE) -C $(PKG_BUILD_DIR) $(TARGET_CONFIGURE_OPTS)
endef

define Package/ddhcpd/install
	$(call Gluon/Build/Install,$(1))
	$(INSTALL_DIR) $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ddhcpd  $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ddhcpdctl $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,ddhcpd))
