KDIR ?= /lib/modules/`uname -r`/build
MODULES_DIR := /lib/modules/`uname -r`/extra

build:
	$(MAKE) -C $(KDIR)  M=$$PWD

install:
	mkdir -p $(MODULES_DIR)
	cp *.ko $(MODULES_DIR)
	depmod

clean:
	$(MAKE) -C $(KDIR) M=$(PWD) clean

.PHONY: build clean install
