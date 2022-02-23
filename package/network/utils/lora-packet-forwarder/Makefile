#
# Copyright (C) 2019 Xue Liu <liuxuenetmail@gmail>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=sx1302_hal
PKG_VERSION:=2.1.0
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://github.com/Lora-net/sx1302_hal/archive/
PKG_SOURCE:=V2.1.0.tar.gz
PKG_HASH:=4b62aa6a83ad449c68fdd844fc35024586c9faabca3c5a90a2544735b380de5b
PKG_MAINTAINER:=Xue Liu <liuxuenetmail@gmail.com>
PKG_LICENSE_FILES:=LICENSE
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
#PKG_BUILD_DIR:=$(BUILD_DIR)/packet_forwarder-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
#include $(INCLUDE_DIR)/cmake.mk

define Package/lora-packet-forwarder
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=LoRaWAN
  TITLE:=Semtech SX1302 packet-forwarder program
#  DEPENDS:=+libloragw +libubox-lua +libuci-lua +dkjson
  DEPENDS:=+libubox-lua +libuci-lua +dkjson
endef

define Package/lora-packet-forwarder/description
  A LoRa packet forwarder is a program running on the host of a LoRa gateway
  that forwards RF packets receive by the concentrator to a server through a
  IP/UDP link, and emits RF packets that are sent by the server.
endef

define Package/lora-packet-forwarder-utils
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=LoRaWAN
  TITLE:=Utilities for lora pakcet forwarder
  DEPENDS:=lora-packet-forwarder
endef

define Package/lora-packet-forwarder/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/packet_forwarder/lora_pkt_fwd $(1)/usr/sbin/lora_pkt_fwd_1302
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/libloragw/test_loragw_* $(1)/usr/sbin/
#	$(INSTALL_BIN) ./files/gen_lora_global_conf $(1)/usr/sbin
#	$(INSTALL_DIR) $(1)/etc/init.d
#	$(INSTALL_BIN) ./files/lora_pkt_fwd.init $(1)/etc/init.d/lora_pkt_fwd
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DATA) ./files/global_conf.json.sx1250.EU868 $(1)/etc/config/global_conf.json.sx1250.EU868
	$(INSTALL_DATA) ./files/reset_lgw.sh $(1)/usr/sbin
#	$(INSTALL_DATA) ./files/lora_pkt_fwd.init $(1)/etc/init.d/lora_pkt_fwd
endef

	#$(INSTALL_BIN) $(PKG_BUILD_DIR)/libloragw/test_loragw_cal_sx125x $(1)/usr/sbin/1302_test_loragw_cal_sx125x
	#$(INSTALL_BIN) $(PKG_BUILD_DIR)/libloragw/test_loragw_capture_ram $(1)/usr/sbin/1302_test_loragw_capture_ram
	#$(INSTALL_BIN) $(PKG_BUILD_DIR)/libloragw/test_loragw_counter $(1)/usr/sbin/1302_test_loragw_counter
	#$(INSTALL_BIN) $(PKG_BUILD_DIR)/libloragw/test_loragw_gps $(1)/usr/sbin/1302_test_loragw_gps
	#$(INSTALL_BIN) $(PKG_BUILD_DIR)/libloragw/test_loragw_hal_rx $(1)/usr/sbin/1302_test_loragw_hal_rx
	#$(INSTALL_BIN) $(PKG_BUILD_DIR)/libloragw/test_loragw_hal_tx $(1)/usr/sbin/1302_test_loragw_hal_tx
	#$(INSTALL_BIN) $(PKG_BUILD_DIR)/libloragw/test_loragw_i2c $(1)/usr/sbin/1302_test_loragw_i2c
	#$(INSTALL_BIN) $(PKG_BUILD_DIR)/libloragw/test_loragw_reg $(1)/usr/sbin/1302_test_loragw_reg
	#$(INSTALL_BIN) $(PKG_BUILD_DIR)/libloragw/test_loragw_spi $(1)/usr/sbin/1302_test_loragw_spi
	#$(INSTALL_BIN) $(PKG_BUILD_DIR)/libloragw/test_loragw_spi_sx1250 $(1)/usr/sbin/1302_test_loragw_spi_sx1250

define Package/lora-packet-forwarder-utils/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bin/util_ack $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bin/util_sink $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bin/util_tx_test $(1)/usr/sbin/pkg_fwd_util_tx_test
endef

$(eval $(call BuildPackage,lora-packet-forwarder))
#$(eval $(call BuildPackage,lora-packet-forwarder-utils))
