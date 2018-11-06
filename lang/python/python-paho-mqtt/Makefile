include $(TOPDIR)/rules.mk

PKG_NAME:=python-paho-mqtt
PKG_VERSION:=1.3.1
PKG_RELEASE:=1
PKG_MAINTAINER:=nobody
PKG_LICENSE:=Eclipse Public License v1.0 / Eclipse Distribution License v1.0

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/eclipse/paho.mqtt.python
PKG_SOURCE_VERSION:=v1.3.1

PKG_SOURCE_SUBDIR:=$(BUILD_VARIANT)-paho-mqtt-$(PKG_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-paho-mqtt-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-paho-mqtt/Default
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  MAINTAINER:=PierreF (https://github.com/PierreF)
  URL:=http://eclipse.org/paho
endef

define Package/python-paho-mqtt
$(call Package/python-paho-mqtt/Default)
  TITLE:=python3-paho-mqtt
  DEPENDS:=+python-light +python-idna +python-logging
  VARIANT:=python
endef

define Package/python3-paho-mqtt
$(call Package/python-paho-mqtt/Default)
  TITLE:=python3-paho-mqtt
  DEPENDS:=+python3-light +python3-idna +python3-logging
  VARIANT:=python3
endef

define Package/python-paho-mqtt/description
  MQTT version 3.1.1 client implementation
endef

define Package/python3-paho-mqtt/description
$(call Package/python-paho-mqtt/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-paho-mqtt))
$(eval $(call BuildPackage,python-paho-mqtt))
$(eval $(call BuildPackage,python-paho-mqtt-src))

$(eval $(call Py3Package,python3-paho-mqtt))
$(eval $(call BuildPackage,python3-paho-mqtt))
$(eval $(call BuildPackage,python3-paho-mqtt-src))
