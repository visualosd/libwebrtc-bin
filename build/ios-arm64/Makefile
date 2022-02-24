include ../../VERSION

BASE_DIR := $(CURDIR)/../..

include ../env.mk

TARGET_OS ?= ios
TARGET_CPU ?= arm64

include ../common.mk

.PHONY: all
all: clean build package

.PHONY: package
package: common-package

.PHONY: copy
copy: common-copy

.PHONY: patch
patch: common-patch

.PHONY: build
build: patch
	cd $(SRC_DIR) && \
	gn gen $(BUILD_DIR) --args='$(CC_WRAPPER) target_os="ios" ios_enable_code_signing=false use_xcode_clang=true target_cpu="$(TARGET_CPU)" enable_ios_bitcode=true enable_stripping=true enable_dsyms=true is_debug=false treat_warnings_as_errors=false $(RTC_USE_H264) rtc_include_tests=false rtc_build_tools=false rtc_build_examples=false rtc_libvpx_build_vp9=false is_component_build=false use_rtti=true libcxx_abi_unstable=false target_environment="device" ios_deployment_target="12.0" use_goma=false rtc_enable_objc_symbol_export=true rtc_libvpx_build_vp9=true enable_stripping=true' && \
	ninja -v -C $(BUILD_DIR)

