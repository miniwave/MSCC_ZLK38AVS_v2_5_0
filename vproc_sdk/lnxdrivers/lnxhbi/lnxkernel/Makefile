include $(ROOTDIR)/Makefile.globals
include $(ROOTDIR)/config.mk

LOCAL_PWD=$(ROOTDIR)/lnxdrivers/lnxhbi/lnxkernel

ccflags-y += -I$(ROOTDIR)/include
ccflags-y += -D$(BUILD_TYPE) 
ccflags-y += -zmuldefs
ccflags-y += -I$(LOCAL_PWD)/inc
ccflags-y += -I$(ROOTDIR)/drivers/hbi
ccflags-y += -I$(ROOTDIR)/drivers/hbi/inc
ccflags-y += -I$($(ROOTDIR))/platform/$(PLATFORM)/images

LIB_DRVPATH := ../../../platform/$(PLATFORM)/driver/ssl
LIB_INPATH := ../../../drivers/hbi
LIB_PATH := ../../../libs
obj-m := hbi.o
hbi-objs := $(LIB_DRVPATH)/hal_port.o $(LIB_INPATH)/hbi_ssl.o $(LIB_INPATH)/hbi_tw.o $(LIB_PATH)/ssl_port.o $(LIB_PATH)/hbi.o hbi_k.o 

all: help
	make -C$(KSRC) M=$(LOCAL_PWD) ARCH=$(ARCH) CROSS_COMPILE=$(CROSS_COMPILE) modules
	make -C$(KSRC) M=$(LOCAL_PWD) modules_install

help:
	@echo "ROOTDIR="$(ROOTDIR)
	@echo "INSTALL_LIB_PATH="$(INSTALL_LIB_PATH)

clean:
	rm -rf   *.o *.ko .*cmd *.mod.c .tmp_versions modules.order Module.symvers *.a ../*.o ../*.mod.* ../.*cmd
