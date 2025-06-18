build:
	dtc -@ -Hepapr -I dts -O dtb -o axzez-interceptor-switch.dtbo axzez-interceptor-switch.dts

install:
	cp axzez-interceptor-switch.dtbo /boot/firmware/overlays/

clean:
	rm -f axzez-interceptor-switch.dtbo

.PHONY: build clean install
