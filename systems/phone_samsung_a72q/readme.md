# samsung galaxy a52/a72 - a52q/a72q

## bootable sd card images

- none yet

## tested systems - working

- samsung galaxy a72 - sm-a725f/ds

## untested systems

- samsung galaxy a72 - other versions
- samsung galaxy a52

## kernel build notes

- https://github.com/hexdump0815/linux-mainline-qcom-msm8998-kernel/blob/main/readme.a72
- before using an own kernel build a postmarketos kernel+initrd=boot.img was used
  - https://github.com/hexdump0815/pmaports-other/tree/main/linux-postmarketos-qcom-sm7125
  - https://github.com/hexdump0815/pmaports-other/tree/main/device-samsung-a52q
  - https://github.com/hexdump0815/pmaports-other/tree/main/device-samsung-a72q

## priority

- experimental mode

## special notes

- this is just some experimental initial draft to support this system in some
  - everything you do based on this is done at your own risk as it can seriously brick the device or do orher unexpected things
  - do not consider playing around with this without a deep understanding about linux, android, the android boot process and partition setup
  way
- this is not very useable yet, still in a very early and experimental phase, but at least i got a debian bookworm system booting well using a self built and installed kernel
  - it is highly recommended to install twrp as recovery on the device to have a last resort in case some installed kernel does not boot
  - currently only running from sd card is considered, it would also be possible to run from the internal ufs storage but this is not handled here yet as the risk to brick the device is even higher this way
  - the boot-a52.img-version or boot-a72.img-version from the boot partition has to be written to the boot partition of the device via some supported method (not sure what works and what would be best: fastboot, heimdall, odin, twrp)
  - usb has been switched to host mode (compared to the peripheral mode of pmos for its usb ethernet) so that it is possible to connect usb devices like ethernet, keyboard, mouse etc. - there is no host power provided by the port, i.e. a powered usb-c hub is required to connect anything (it looks like the device is powered properly this way too)
  - the usb port is usb 2 only, so dp alt mode over type c is not possible to connect an external dp/hdmi monitor but displaylink usb 2 adapters (using the linux udl driver) are working (tested to be working, but refresh and performance is rather slow - even the gpu seems to get properly connected to the udl device as well but is slow as well in this setup)
- a1 rated sd cards are highly recommended as otherwise the performance will be bad due to bad random disk io
