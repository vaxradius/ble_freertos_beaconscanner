TARGET := ble_freertos_beaconscanner
COMPILERNAME := Keil
PROJECT := ble_freertos_beaconscanner_Keil
CONFIG := bin

SHELL:=/bin/bash
#### Required Executables ####
K := $(shell type -p UV4.exe)
RM := $(shell which rm 2>/dev/null)

ifeq ($(K),)
all clean:
	$(info Tools w/$(COMPILERNAME) not installed.)
	$(RM) -rf bin
else

all: directories binary

.PHONY: binary
binary:
	UV4.exe -b -t "ble_freertos_beaconscanner" ble_freertos_fit_lp.uvprojx -j0 || [ $$? -eq 1 ]

directories: $(CONFIG)

$(CONFIG):
	@mkdir -p $@

clean:
	@echo Cleaning... ;\
	$(RM) -rf $(CONFIG)


../../../../../mcu/apollo3/hal/keil/bin/libam_hal.lib:
	$(MAKE) -C ../../../../../mcu/apollo3/hal

../../../bsp/keil/bin/libam_bsp.lib:
	$(MAKE) -C ../../../bsp

endif
.PHONY: all clean directories

