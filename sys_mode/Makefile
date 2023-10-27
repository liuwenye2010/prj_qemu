

all: build run 


build: 
	echo "cross compile the u-boot"
	export ARCH=arm CROSS_COMPILE=arm-linux-gnueabi- && make -C u-boot
run:
	echo "run with QEMU"
	cd u-boot && qemu-system-arm -M vexpress-a9 -m 128M -nographic -kernel u-boot

image:
	echo "create a SPI flash image" 
	cd u-boot && dd if=/dev/zero of=test.img count=32 bs=1M && dd if=u-boot.bin of=test.img conv=notrunc


debug:
	echo "gdb debug with QEMU"
	cd u-boot && qemu-system-arm -M vexpress-a9 -m 128M -nographic -kernel u-boot -s -S
	echo "### Please >gdb-multiarch  uboot  -ex "target remote localhost:1234"
	
	
#debug2: image
#	cd u-boot && qemu-system-arm -M ast2500-evb -nographic -drive file=test.img,format=raw,if=mtd,readonly -s -S
	
gdb:
	cd u-boot && gdb-multiarch u-boot -ex "target remote localhost:1234"