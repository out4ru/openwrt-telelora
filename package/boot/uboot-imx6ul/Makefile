#
# Copyright (C) 2013-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

#PKG_VERSION:=2017.03
#PKG_RELEASE:=1

#-------------------------------------------------
PKG_VERSION:=2020.04
PKG_RELEASE:=$(AUTORELEASE)
PKG_HASH:=fe732aaf037d9cc3c0909bad8362af366ae964bbdac6913a34081ff4ad565372
#------------------------------------------------

#PKG_SOURCE_PROTO:=git
#PKG_SOURCE_URL:=https:///github.com/Freescale/u-boot-fslc.git
#PKG_SOURCE_VERSION:=02e2e1cb19fcdcb107b73970a1a1230b93f5d40e
#PKG_HASH:=52fed6ce16e0c4a50e2cd4defdf9097a

include $(INCLUDE_DIR)/u-boot.mk
include $(INCLUDE_DIR)/package.mk

define U-Boot/Default
  BUILD_TARGET:=imx6ul
  UBOOT_IMAGE:=u-boot.imx
endef


define U-Boot/imx6ull-ev-m2-simple
  NAME:=Evodbg EV-iMX6UL-M2 Simple
endef

define U-Boot/imx6ull-ev-m2-twin
  NAME:=Evodbg EV-iMX6UL-M2 Twin
endef

define U-Boot/imx6ull-ev-nano-tira
  NAME:=Evodbg EV-iMX6UL-NANO Tira
endef

define U-Boot/imx6ull-o4-nano-telelora-v2
  NAME:=OUT4 O4-iMX6ULL TeleLoRa-V2
endef

define U-Boot/imx6ull-o4-nano-tempest
  NAME:=OUT4 O4-iMX6ULL-NANO Tempest
endef

define U-Boot/imx6ull-o4-sodimm-tron
  NAME:=OUT4 O4-iMX6ULL-SODIMM Tron
endef




UBOOT_TARGETS := \
	imx6ull-ev-m2-simple \
	imx6ull-ev-m2-twin \
	imx6ull-ev-nano-tira \
	imx6ull-o4-nano-telelora-v2 \
	imx6ull-o4-nano-tempest \
	imx6ull-o4-sodimm-tron

UBOOT_MAKE_FLAGS += u-boot.imx

define Build/InstallDev
	$(INSTALL_DIR) $(STAGING_DIR_IMAGE)
	$(foreach img,$(UBOOT_IMAGE), \
		$(CP) $(PKG_BUILD_DIR)/$(img) $(STAGING_DIR_IMAGE)/$(BUILD_VARIANT)-$(img); \
	)
endef

$(eval $(call BuildPackage/U-Boot))
