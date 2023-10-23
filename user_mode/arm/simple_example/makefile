##sudo apt install gcc-arm-linux-gnueabi
##sudo apt install qemu-user
CC=arm-linux-gnueabi-gcc
all: build run
build:
	$(CC) -o example_static -static main.c
	$(CC) -o example                main.c
	file     example_static
	file     example
	echo "build done"
run:
	qemu-arm  example_static
	echo "run static done"
	qemu-arm -L /usr/arm-linux-gnueabi/  example
	echo "run dynamic done"