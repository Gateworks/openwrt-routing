#
# Copyright (C) 2006-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mcproxy
PKG_SOURCE_VERSION:=6638aa9aabd2ccdde8915b61a8e0fb995b1f91a3
PKG_VERSION:=2014-05-31-$(PKG_SOURCE_VERSION)
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/mcproxy/mcproxy.git
PKG_MAINTAINER:=Steven Barth <cyrus@openwrt.org>
PKG_LICENSE:=GPL-2.0+

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/mcproxy
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Routing and Redirection
  TITLE:=Multicast Proxy for IGMP/MLD
  URL:=http://mcproxy.realmv6.org
  DEPENDS:=+libpthread +libstdcpp @(!GCC_VERSION_4_4&&!GCC_VERSION_4_6)
endef

define Package/mcproxy/description
 mcproxy is a free & open source implementation of the IGMP/MLD proxy function (see  RFC 4605) for Linux systems.
 It operates on the kernel tables for multicast routing and allows for multiple instantiations,
 as well as dynamically changing downstream interfaces.
endef

define Package/mcproxy/conffiles
/etc/mcproxy.conf
endef

define Package/mcproxy/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_CONF) ./files/mcproxy.conf $(1)/etc
	$(INSTALL_BIN) ./files/mcproxy.init $(1)/etc/init.d/mcproxy
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mcproxy-bin $(1)/usr/sbin/mcproxy
endef

$(eval $(call BuildPackage,mcproxy))
