# DKMS package for Axzez Interceptor Board on RaspberrryPI OS

For this to work you need to a kernel that has DSA enabled (see https://github.com/raspberrypi/linux/issues/6899).
As this writing only the newest kernel (6.12.34-1+rpt1~bookworm) has this module enabled.
In order successfully build the kernel modules and the device-tree files you need to install a couple of
packages:

```
apt update
apt install linux-headers-rpi-v8 linux-headers-rpi-2712 dkms device-tree-compiler
```

Now download the deb package from the release page and install it with:

```
dpkg -i axzez-interceptor-switch-dkms_6.12-1_all.deb
```

This will build the necessary kernel modules as well as the device tree overlay.
The device tree overlay has 4 parameters that allow you to override the names of the 4
DSA interfaces that will be created once the overlay is loaded, i.e. by adding the line:

```
dtoverlay=axzez-interceptor-switch,port1name=svc0,port2name=iot0,port3name=unused,port4name=mgmt0
```

to `/boot/firmware/config.txt`.
