#
# Copyright (C) 2020-2022 HandsomeMod Project
# Copyright (C) 2016-2024 AlienWolfX
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qcom-firmware
PKG_VERSION:=uz801
PKG_RELEASE:=1

PKG_SOURCE_URL:=http://192.168.1.14:8000/
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_HASH:=36427875d0324b64f6eb9ee71dbc447b

PKG_MAINTAINER:=Allen Cruiz <allengabrielle.cruiz@carsu.edu.ph>
STRIP:=:

include $(INCLUDE_DIR)/package.mk

define Package/qcom-firmware-default
  SECTION:=firmware
  CATEGORY:=Firmware
endef

define Build/Compile
	mkdir $(PKG_BUILD_DIR)/bogartx-uz801
# 	mount -o loop -t vfat $(PKG_BUILD_DIR)/uz801-modem-philippines.bin /mnt
# 	tar -xvf $(PKG_BUILD_DIR)/uz801-modem-philippines.bin -C $(PKG_BUILD_DIR)/bogartx-uz801
	mcopy -i $(PKG_BUILD_DIR)/uz801-modem-philippines.bin -p -m -v \
		::image/mba.mbn ::image/modem.* ::image/wcnss.* ::image/modem_pr/mcfg/configs/mcfg_sw/generic/common/default/default/* $(PKG_BUILD_DIR)/bogartx-uz801	
endef


define Package/qcom-msm8916-bogartx-uz801-wcnss-firmware
  $(Package/qcom-firmware-default)
  TITLE:=BogartX UZ801 WIFI & Bluetooth firmware v3.2
endef

define Package/qcom-msm8916-wcnss-bogartx-uz801-nv
  $(Package/qcom-firmware-default)
  TITLE:=BogartX msm8916 WIFI nv data for UZ801 v3.2
endef

define Package/qcom-msm8916-modem-bogartx-uz801-firmware
  $(Package/qcom-firmware-default)
  TITLE:=BogartX msm8916 modem firmware for UZ801 v3.2
endef

define Package/qcom-msm8916-bogartx-uz801-wcnss-firmware/install
	$(INSTALL_DIR) $(1)/lib/firmware
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/bogartx-uz801/wcnss.* \
		$(1)/lib/firmware
endef


define Package/qcom-msm8916-wcnss-bogartx-uz801-nv/install
	$(INSTALL_DIR) $(1)/lib/firmware/wlan/prima
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/uz801-qcom-wlan-nv.bin \
		$(1)/lib/firmware/wlan/prima/WCNSS_qcom_wlan_nv.bin
endef


define Package/qcom-msm8916-modem-bogartx-uz801-firmware/install
	$(INSTALL_DIR) $(1)/lib/firmware
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/bogartx-uz801/mba.mbn \
		$(1)/lib/firmware
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/bogartx-uz801/mcfg_sw.mbn \
		$(1)/lib/firmware
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/bogartx-uz801/modem.* \
		$(1)/lib/firmware
endef

$(eval $(call BuildPackage,qcom-msm8916-bogartx-uz801-wcnss-firmware))
$(eval $(call BuildPackage,qcom-msm8916-wcnss-bogartx-uz801-nv))
$(eval $(call BuildPackage,qcom-msm8916-modem-bogartx-uz801-firmware))
