#
# Copyright (C) 2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=qrtr
PKG_RELEASE:=5.8

include $(INCLUDE_DIR)/package.mk
include 

define KernelPackage/qrtr
  SUBMENU:=Network Support
  TITLE:=Qualcomm IPC Router support
  FILES:=$(PKG_BUILD_DIR)/qrtr.ko
  AUTOLOAD:=$(call AutoProbe,qrtr)
endef

define KernelPackage/qrtr/description
 Qualcomm IPC Router support
endef

define KernelPackage/qrtr-smd
  SUBMENU:=Network Support
  TITLE:=SMD IPC Router channels
  DEPENDS:=+kmod-qrtr @TARGET_qualcommax
  KCONFIG:=CONFIG_QRTR_SMD
  FILES:= $(PKG_BUILD_DIR)/qrtr-smd.ko
  AUTOLOAD:=$(call AutoProbe,qrtr-smd)
endef

define KernelPackage/qrtr-smd/description
 SMD IPC Router channels
endef

define KernelPackage/qrtr-mhi
  SUBMENU:=Network Support
  TITLE:=MHI IPC Router channels
  DEPENDS:=+kmod-mhi-bus +kmod-qrtr
  KCONFIG:=CONFIG_QRTR_MHI
  FILES:= $(PKG_BUILD_DIR)/qrtr-mhi.ko
  AUTOLOAD:=$(call AutoProbe,qrtr-mhi)
endef

define KernelPackage/qrtr-mhi/description
 MHI IPC Router channels
endef

include $(INCLUDE_DIR)/kernel-defaults.mk

define Build/Compile
	$(KERNEL_MAKE) M="$(PKG_BUILD_DIR)" modules
endef

$(eval $(call KernelPackage,qrtr))
$(eval $(call KernelPackage,qrtr-smd))
$(eval $(call KernelPackage,qrtr-mhi))