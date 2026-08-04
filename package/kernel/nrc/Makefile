include $(TOPDIR)/rules.mk

PKG_NAME:=nrc
PKG_VERSION:=1.3.2
PKG_RELEASE:=1

PKG_MAINTAINER:=Newracom
PKG_LICENSE:=GPL-2.0-only
PKG_LICENSE_FILES:=LICENSE

STAMP_CONFIGURED_DEPENDS := $(STAGING_DIR)/usr/include/mac80211-backport/backport/autoconf.h

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/nrc
  SUBMENU:=Wireless Drivers
  TITLE:=Newracom NRC7394 802.11ah wireless driver
  DEPENDS:=+TARGET_bcm27xx:kmod-spi-bcm2835 +kmod-mac80211
  FILES:=$(PKG_BUILD_DIR)/nrc.ko
  AUTOLOAD:=$(call AutoProbe,nrc)
endef

define KernelPackage/nrc/description
  Newracom NRC7394 802.11ah Wi-Fi HaLow host driver and target firmware.
endef

define KernelPackage/nrc/install
	$(INSTALL_DIR) $(1)/lib/firmware
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/firmware/nrc7394_bd.dat \
		$(1)/lib/firmware/nrc_bd.dat
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/firmware/nrc7394_cspi.bin \
		$(1)/lib/firmware/uni_s1g.bin
endef

NOSTDINC_FLAGS := \
	$(KERNEL_NOSTDINC_FLAGS) \
	-I$(PKG_BUILD_DIR) \
	-I$(STAGING_DIR)/usr/include/mac80211-backport/uapi \
	-I$(STAGING_DIR)/usr/include/mac80211-backport \
	-I$(STAGING_DIR)/usr/include/mac80211/uapi \
	-I$(STAGING_DIR)/usr/include/mac80211 \
	-include backport/autoconf.h \
	-include backport/backport.h \
	-include $(TOOLCHAIN_DIR)/include/linux/genetlink.h

define Build/Compile
	+$(KERNEL_MAKE) $(PKG_JOBS) \
		$(PKG_MAKE_FLAGS) \
		M="$(PKG_BUILD_DIR)" \
		NOSTDINC_FLAGS="$(NOSTDINC_FLAGS)" \
		modules
endef

$(eval $(call KernelPackage,nrc))
