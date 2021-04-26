#### buildroot for linux kernel debugging
#### setting
- `make qemu_aarch64_virt_defconfig`
- `make menuconfig`
  - Toolchain: gdb
  - Kernel: Kernel format
  - Debugging: fio, iozone
  - Hardware Handling: nvme, pciutils
  - Libraries: libaio
  - Filesystem images: exact size
- `build linux`
  - `make linux-rebuild` 

#### make nvme img
```shell
dd if=/dev/zero of=nvme.img oflag=direct bs=4M count=1024
mkfs --type=ext4 /dev/nvme.img
losetup /dev/loop0 nvme.img #??
mkfs --type=ext4 /dev/loop0
```