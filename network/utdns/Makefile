#

include $(TOPDIR)/rules.mk

PKG_NAME:=utdns
PKG_RELEASE:=1

PKG_SOURCE_URL=https://github.com/chrislimpach/utdns.git
PKG_MIRROR_HASH=7b2a160af68d9c70febc5aa6b368235eea2e27cbc4d4a8c056b1b6bd040d653c
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v1.1-cl1

PKG_MAINTAINER:=Christian Limpach <Christian.Limpach@gmail.com>
PKG_LICENSE:=GPL-3.0

PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
#include $(INCLUDE_DIR)/cmake.mk

define Package/utdns
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Routing and Redirection
  TITLE:=Proxy UDP/DNS to TCP/DNS
#  DEPENDS:=+libubox
endef

#TARGET_CFLAGS += -I$(STAGING_DIR)/usr/include

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C $(PKG_BUILD_DIR) \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		CC="$(TARGET_CC)" \
		install
endef

define Package/utdns/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/utdns $(1)/usr/sbin/utdns
#	$(INSTALL_DIR) $(1)/etc/init.d
#	$(INSTALL_BIN) ./files/utdns.init $(1)/etc/init.d/utdns
endef

$(eval $(call BuildPackage,utdns))
