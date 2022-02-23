#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/image.mk

#################################################
# Images
#################################################

DEVICE_VARS += MKUBIFS_OPTS UBOOT BOOT_SCRIPT


LS_SYSUPGRADE_IMAGE_SIZE = 49m

#################################################
# Devices
#################################################


KERNEL_LOADADDR=0x10008000

define Device/Default
  PROFILES := Generic
#  PROFILES := imx6ull
  FILESYSTEMS := ext4
  KERNEL_INSTALL := 1
  KERNEL_SUFFIX := -zImage
  KERNEL_NAME := zImage
#  KERNEL_PREFIX := $$(IMAGE_PREFIX)
#KERNEL_PREFIX := zImage-
  KERNEL := kernel-bin | uImage none
#  IMAGE/dtb := install-dtb
IMAGES :=
IMAGE/sysupgrade.bin = \
    ls-append-dtb $$(DEVICE_DTS) | pad-to 1M | \
    append-kernel | pad-to 17M | \
    append-rootfs | pad-rootfs | \
    check-size $(LS_SYSUPGRADE_IMAGE_SIZE) | append-metadata
endef



define Device/ev-imx6ull-m2-simple
  DEVICE_TITLE := EV-iMX6ULL-M2-SIMPLE
  DEVICE_VENDOR := Evodbg
  DEVICE_MODEL := ev-imx6ull-m2-simple
  DEVICE_DTS := imx6ull-ev-m2-simple
    IMAGES := dtb
    IMAGE/dtb := install-dtb
    KERNEL := kernel-bin | install-dtb
endef
TARGET_DEVICES += ev-imx6ull-m2-simple

define Device/ev-imx6ull-m2-twin
  DEVICE_TITLE := EV-iMX6ULL-M2-TWIN
  DEVICE_VENDOR := Evodbg
  DEVICE_MODEL := ev-imx6ull-m2-twin
  DEVICE_DTS := imx6ull-ev-m2-twin
  UBOOT := o4-imx6ul-sodimm
    IMAGES := dtb
    IMAGE/dtb := install-dtb
    KERNEL := kernel-bin | install-dtb
endef
TARGET_DEVICES += ev-imx6ull-m2-twin

define Device/ev-imx6ul-nano-tira
  DEVICE_TITLE := EV-iMX6ULL-NANO-TIRA
  DEVICE_VENDOR := Evodbg
  DEVICE_MODEL := ev-imx6ul-nano-tira
  DEVICE_DTS := imx6ull-ev-nano-tira
    IMAGES := dtb
    IMAGE/dtb := install-dtb
    KERNEL := kernel-bin | install-dtb
endef
TARGET_DEVICES +=  ev-imx6ul-nano-tira

define Device/o4-imx6ull-nano-telelora-v2
  DEVICE_TITLE := O4-iMX6ULL-NANO-TELELORA-V2
  DEVICE_VENDOR := Out4
  DEVICE_MODEL := o4-imx6ull-nano-telelora-v2
  DEVICE_DTS := imx6ull-o4-nano-telelora-v2
    IMAGES := dtb
    IMAGE/dtb := install-dtb
    KERNEL := kernel-bin | install-dtb
endef
TARGET_DEVICES += o4-imx6ull-nano-telelora-v2

define Device/o4-imx6ull-nano-tempest
  DEVICE_TITLE := O4-iMX6ULL-NANO-TEMPEST
  DEVICE_VENDOR := Out4
  DEVICE_MODEL := o4-imx6ull-nano-tempest
  DEVICE_DTS := imx6ull-o4-nano-tempest
    IMAGES := dtb
    IMAGE/dtb := install-dtb
    KERNEL := kernel-bin | install-dtb
endef
TARGET_DEVICES += o4-imx6ull-nano-tempest

define Device/o4-imx6ull-nano-sodimm-tron
  DEVICE_TITLE := O4-iMX6ULL-SODIMM-TRON
  DEVICE_VENDOR := Out4
  DEVICE_MODEL := Device/o4-imx6ull-sodimm-tron
  DEVICE_DTS := imx6ull-o4-sodimm-tron
    IMAGES := dtb
    IMAGE/dtb := install-dtb
    KERNEL := kernel-bin | install-dtb
endef
TARGET_DEVICES += o4-imx6ull-nano-sodimm-tron

$(eval $(call BuildImage))
