#
# Copyright (C) 2006-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=keepalived
PKG_VERSION:=2.0.7
PKG_RELEASE:=3

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://www.keepalived.org/software
PKG_HASH:=bce45d6d5cf3620bfd88472ec839a75b5a14a54fda12d09e890670244873b8ab

PKG_LICENSE:=GPL-2.0+
PKG_LICENSE_FILES:=COPYING
PKG_MAINTAINER:=Ben Kelly <ben@benjii.net> \
		Florian Eckert <fe@dev.tdt.de>

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/kernel.mk

define Package/keepalived
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Failover and monitoring daemon for LVS clusters
  URL:=http://www.keepalived.org/
  DEPENDS:= \
    +libopenssl \
    +libip4tc \
    +IPV6:libip6tc \
    +libxtables \
    +kmod-macvlan \
    +libmagic \
    +libnl-route \
    +libnfnetlink \
    +kmod-nf-ipvs
endef

define Package/keepalived/description
 Failover and monitoring daemon for Linux Virtual Server (LVS) clusters.
endef

define Package/keepalived/conffiles
/etc/keepalived/keepalived.conf
/etc/config/keepalived
/etc/keepalived.user
endef

CONFIGURE_ARGS+= \
	--disable-libipset \
	--disable-libnl \
	--enable-sha1 \
	--disable-snmp \
	--with-kernel-dir="$(LINUX_DIR)/$(LINUX_UAPI_DIR)"

MAKE_FLAGS += \
		STRIP="/bin/true" \

define Package/keepalived/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(CP) $(PKG_INSTALL_DIR)/usr/sbin/keepalived $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/genhash $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/keepalived
	$(CP) $(PKG_INSTALL_DIR)/etc/keepalived/keepalived.conf $(1)/etc/keepalived/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/keepalived.init $(1)/etc/init.d/keepalived
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/keepalived.config $(1)/etc/config/keepalived
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_CONF) ./files/keepalived.user $(1)/etc/keepalived.user
	$(INSTALL_DIR) $(1)/etc/hotplug.d/keepalived
	$(INSTALL_DATA) ./files/hotplug-user $(1)/etc/hotplug.d/keepalived/01-user
endef

$(eval $(call BuildPackage,keepalived))
