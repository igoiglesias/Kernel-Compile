# Kernel-Compile
How to compile the linux kernel 

## Install dependencies
	sudo apt-get install libncurses-dev flex bison openssl libssl-dev dkms libelf-dev libudev-dev libpci-dev libiberty-dev autoconf

## Download
	wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.12.14.tar.xz

## Decompress
	sudo tar -xvf linux-5.12.14.tar.xz

## Organize a bit
	mkdir kernel/
	cp -r linux-5.12.14 kernel  
	cd  kernel/linux-5.12.14

## Generatte or copy config file
	cp /boot/config-$(uname -r) .config
	### or
	make localmodconfig

## Personalize
	make menuconfig

## Compile 
	make -j8 KDEB_PKGVERSION=1.0 deb-pkg

## Install
	sudo dpkg -i ../linux*.deb

## Remove (If something goes wrong)
	sudo apt purge linux-image-5.12.14
