#
# Copyright (C) 2015 - 2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libpri
PKG_VERSION:=1.6.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://downloads.asterisk.org/pub/telephony/libpri/releases
PKG_HASH:=d4d1a62766695455f1b616f5f7603458e6d23df787ebabc31ffda1c6298d0509
PKG_MAINTAINER:=Daniel Golle <daniel@makrotopia.org>

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libpri
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=libpri Primary Rate ISDN implementation
  URL:=http://www.asterisk.org/
  DEPENDS:=+dahdi-tools-libtonezone
endef

define Package/libpri/description
	libpri is a C implementation of the Primary Rate ISDN specification. It was
	based on the Bellcore specification SR-NWT-002343 for National ISDN. As of
	May 12, 2001, it has been tested work with NI-2, Nortel DMS-100, and
	Lucent 5E Custom protocols on switches from Nortel and Lucent.
endef

MAKE_FLAGS += \
	OSARCH=Linux \
	LDCONFIG=ldconfig

define Build/Configure
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/include/*.h $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libpri*.a $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libpri*.so* $(1)/usr/lib/
endef

define Package/libpri/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libpri*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libpri))
