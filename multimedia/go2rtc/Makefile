include $(TOPDIR)/rules.mk

PKG_NAME:=go2rtc
PKG_VERSION:=1.9.9
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/AlexxIT/go2rtc/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=0afb5a9f0cdbd696193288197cfb5ebf44d085f631e7326cc0465026fe3b9196

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Vladimir Ermakov <vooon341@gmail.com>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=github.com/AlexxIT/go2rtc
GO_PKG_EXCLUDES:=examples/

include $(INCLUDE_DIR)/package.mk
include ../../lang/golang/golang-package.mk

define Package/go2rtc
  SECTION:=multimedia
  CATEGORY:=Multimedia
  TITLE:=go2rtc camera streaming
  URL:=https://github.com/AlexxIT/go2rtc
  DEPENDS:=$(GO_ARCH_DEPENDS) +ffmpeg
  USERID:=go2rtc:go2rtc
endef

define Package/go2rtc/description
  Ultimate camera streaming application with support RTSP, WebRTC, HomeKit, FFmpeg, RTMP, etc.
endef

define Package/go2rtc/conffiles
/etc/go2rtc.yaml
endef

define Package/go2rtc/install
	$(call GoPackage/Package/Install/Bin,$(1))

	$(INSTALL_DIR) $(1)/etc/
	$(INSTALL_CONF) $(CURDIR)/files/go2rtc.yaml $(1)/etc/go2rtc.yaml
	$(INSTALL_DIR) $(1)/etc/init.d/
	$(INSTALL_BIN) $(CURDIR)/files/go2rtc.init $(1)/etc/init.d/go2rtc
endef

$(eval $(call BuildPackage,go2rtc))
