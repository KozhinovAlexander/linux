# SPDX-License-Identifier: GPL-2.0
#
#  Makefile for the Linux Controller Area Network USB drivers.
#

# obj-$(CONFIG_CAN_8DEV_USB) += usb_8dev.o
# obj-$(CONFIG_CAN_EMS_USB) += ems_usb.o
# obj-$(CONFIG_CAN_ESD_USB) += esd_usb.o
# obj-$(CONFIG_CAN_ETAS_ES58X) += etas_es58x/
# obj-$(CONFIG_CAN_F81604) += f81604.o
obj-$(CONFIG_CAN_GS_USB) += gs_usb.o
# obj-$(CONFIG_CAN_KVASER_USB) += kvaser_usb/
# obj-$(CONFIG_CAN_MCBA_USB) += mcba_usb.o
# obj-$(CONFIG_CAN_PEAK_USB) += peak_usb/
# obj-$(CONFIG_CAN_UCAN) += ucan.o

build:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

install:
# Create .ko.zst file
	rm -f gs_usb.ko.zst
	zstd -19 gs_usb.ko
# Install the .ko.zst file
	rm -f /lib/modules/$(shell uname -r)/kernel/drivers/net/can/usb/gs_usb.ko.zst
	install -m 644 gs_usb.ko.zst /lib/modules/$(shell uname -r)/kernel/drivers/net/can/usb
# Update module dependencies
	depmod -a
	modprobe -r gs_usb
	modprobe gs_usb

# uninstall:
# 	rm -f /lib/modules/$(shell uname -r)/kernel/drivers/net/can/usb/extra/gs_usb.ko.zst
# 	depmod -a
