# Build missing kernel modules for Axzez Interceptor Board RaspberrryPI OS

The plan is to turn this into a DKMS package but for now this needs to be built manually.
See https://github.com/raspberrypi/linux/issues/6899 for details.

```
rpi-update pulls/6907
reboot
apt-get install bc bison flex libssl-dev libncurses5-dev make gcc patch git
cd /dev/shm
git clone --depth 1 --single-branch https://github.com/raspberrypi/linux.git
cd linux
git fetch --depth=1 origin pull/6907/head:pr-6907
git checkout pr-6907
KERNEL=kernel8
make bcm2711_defconfig
make modules_prepare
cd /lib/modules/6.12.33-v8+/
ln -sf /dev/shm/linux build
cd /dev/shm
git clone --depth 1 --single-branch https://github.com/equinox0815/rpi-cm4-axzez-interceptor.git
cd rpi-cm4-axzez-interceptor/src
make build KBUILD_MODPOST_WARN=1
make install
cd ../device-tree
make build
make install
```

The device tree oberlay has 4 parameters that allow you to override the interface names of the 4
DSA interface that will be created once the overlay is loaded, i.e.:

```
dtoverlay=axzez-interceptor-switch,port1name=svc0,port2name=iot0,port3name=unused,port4name=mgmt0
```

