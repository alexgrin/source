include $(TOPDIR)/rules.mk

PKG_NAME:=usign
PKG_VERSION:=2015-07-04
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=$(LEDE_GIT)/project/usign.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=ef6419142a3b0fbcddcccf536e3c1880302c6f89
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.xz
PKG_MIRROR_HASH:=170f85fb49ec3e698fbeb57e9429de3b561c22a23106fc5484ba83010178550c
CMAKE_INSTALL:=1
PKG_CHECK_FORMAT_SECURITY:=1
PKG_USE_MIPS16:=0

PKG_LICENSE:=ISC
PKG_LICENSE_FILES:=

PKG_MAINTAINER:=Felix Fietkau <nbd@nbd.name>

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/cmake.mk

HOST_BUILD_PREFIX:=$(STAGING_DIR_HOST)

define Package/usign
  SECTION:=base
  CATEGORY:=Base system
  DEPENDS:=+libubox
  TITLE:=OpenWrt signature verification utility
endef

CMAKE_OPTIONS += \
	-DUSE_LIBUBOX=on

define Package/usign/install
	$(INSTALL_DIR) $(1)/usr/bin

	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/usign $(1)/usr/bin
	ln -s usign $(1)/usr/bin/signify
endef

$(eval $(call BuildPackage,usign))
$(eval $(call HostBuild))
