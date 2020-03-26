TARGET := ble_freertos_beaconscanner
COMPILERNAME := iar
PROJECT := ble_freertos_beaconscanner_iar
CONFIG := bin
AM_SoftwareRoot ?= ../../../..

SHELL:=/bin/bash
#### Required Executables ####
K := $(shell type -p IarBuild.exe)
RM = $(shell which rm 2>/dev/null)

ifeq ($(K),)
all clean:
	$(info Tools w/$(COMPILERNAME) not installed.)
	$(RM) -rf bin
else

all: directories binary

.PHONY: binary
binary:
	IarBuild.exe ble_freertos_beaconscanner.ewp -make Debug -log info

directories: $(CONFIG)

$(CONFIG):
	@mkdir -p $@

clean:
	@echo Cleaning... ;\
	IarBuild.exe ble_freertos_beaconscanner.ewp -clean Debug -log all


../../../bsp/iar/bin/libam_bsp.a:
	$(MAKE) -C ../../../bsp

../../../../../mcu/apollo3/hal/iar/bin/libam_hal.a:
	$(MAKE) -C ../../../../../mcu/apollo3/hal

endif
.PHONY: all clean directories
