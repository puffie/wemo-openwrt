include $(TOPDIR)/rules.mk

PKG_NAME:=cli_app
PKG_VERSION:=1.3.2
PKG_RELEASE:=1
PKG_MAINTAINER:=Newracom
PKG_LICENSE:=MIT

include $(INCLUDE_DIR)/package.mk


define Package/cli_app
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Newracom NRC7394 command-line utility
endef

define Package/cli_app/description
  Control the Newracom NRC7394 Wi-Fi HaLow module over netlink.
endef


define Build/Configure
endef

define Build/Compile
	$(TARGET_CC) $(TARGET_CFLAGS) \
		-o $(PKG_BUILD_DIR)/cli_app \
		$(PKG_BUILD_DIR)/cli_cmd.c \
		$(PKG_BUILD_DIR)/cli_history.c \
		$(PKG_BUILD_DIR)/cli_netlink.c \
		$(PKG_BUILD_DIR)/cli_util.c \
		$(PKG_BUILD_DIR)/main.c
endef


define Package/cli_app/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/cli_app $(1)/usr/bin/cli_app
endef

$(eval $(call BuildPackage,cli_app))
