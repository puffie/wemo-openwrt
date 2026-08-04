include $(TOPDIR)/rules.mk

PKG_NAME:=rpi-rootfs-expand
PKG_VERSION:=1
PKG_RELEASE:=1

PKG_MAINTAINER:=Newracom
PKG_LICENSE:=GPL-2.0-only

include $(INCLUDE_DIR)/package.mk

define Package/rpi-rootfs-expand
  SECTION:=base
  CATEGORY:=Base system
  TITLE:=Automatic Raspberry Pi root filesystem expansion
  DEPENDS:=@TARGET_bcm27xx +parted +resize2fs +tune2fs
endef

define Package/rpi-rootfs-expand/description
  Expand the Raspberry Pi root partition and ext4 filesystem to fill the
  installation media. A reboot is requested only after changing the partition
  table; an already expanded partition is resized online.
endef

define Build/Compile
endef

define Package/rpi-rootfs-expand/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/rootfs-expand.init $(1)/etc/init.d/rootfs-expand
endef

$(eval $(call BuildPackage,rpi-rootfs-expand))
