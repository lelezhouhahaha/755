.PHONY: all middleware

USE_MDM_PLATFORM := 1

COMPILER_PREFIX := arm-linux-gnueabihf-
TOOLCHAIN_MAKEFILE := toolchain-linux-cross-compile.cmake
TARGET := pclin-generic-arm

OUTPUT_DIR := output/host

SYNERGY_ROOT_DIR := $(shell pwd)

SYNERGY_MIDDLEWARE_DIR := $(SYNERGY_ROOT_DIR)/synergy-middleware
SYNERGY_MIDDLEWARE_COMMON_DIR := $(SYNERGY_MIDDLEWARE_DIR)/common
SYNERGY_MIDDLEWARE_PORTING_DIR := $(SYNERGY_MIDDLEWARE_DIR)/platform/mdm/porting

all: middleware 

export TARGET

CMAKE_BT_DEFINITION += -DCMAKE_VERBOSE_MAKEFILE:STRING=1 \
			-DCMAKE_TOOLCHAIN_FILE:FILEPATH=$(SYNERGY_MIDDLEWARE_DIR)/common/build/$(TOOLCHAIN_MAKEFILE) \
			-DUSE_MDM_PLATFORM:BOOL=$(USE_MDM_PLATFORM)

middleware:
# copy source code under './platform/mdm/porting' into './common' folder
	cp -rf $(SYNERGY_MIDDLEWARE_PORTING_DIR)/* $(SYNERGY_MIDDLEWARE_COMMON_DIR)

	mkdir $(SYNERGY_MIDDLEWARE_DIR)/$(OUTPUT_DIR) -p
	cd $(SYNERGY_MIDDLEWARE_DIR)/$(OUTPUT_DIR)&&cmake -G 'Unix Makefiles' $(SYNERGY_MIDDLEWARE_COMMON_DIR) $(CMAKE_BT_DEFINITION)
	make -C $(SYNERGY_MIDDLEWARE_DIR)/$(OUTPUT_DIR) all
