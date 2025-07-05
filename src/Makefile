KVERSION ?= $(shell uname -r)

KDIR := /lib/modules/$(KVERSION)/build
MODULES_DIR := /lib/modules/$(KVERSION)/extra

build:
	$(MAKE) -C $(KDIR)  M=$$PWD

install:
	mkdir -p $(MODULES_DIR)
	cp *.ko $(MODULES_DIR)
	depmod

clean:
	$(MAKE) -C $(KDIR) M=$(PWD) clean

.PHONY: build clean install
