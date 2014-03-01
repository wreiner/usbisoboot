usbisoboot
==========

Booting multiple ISOs from an USB stick using Grub

Based on the information found at http://www.panticz.de/MultiBootUSB
	1. Create a partition on the usb stick (partition type 0x0C)
	2. Create filesystem on the partition
		mkfs.vfat -n isostick /dev/sdX1
	3. Mount the filesystem
		mount /dev/sdX1 /mnt/isostick
	4. Install grub2 on usb drive
		grub-install --no-floppy --recheck --root-directory=/mnt /dev/sdX
    5. Create the directory structure
        mkdir -p /mnt/boot/{group,iso}
	6. Copy the file grub/grub.cfg onto the stick
		cp grub.cfg /mnt/isostick/boot/grub/grub.cfg
	7. Copy all needed iso files on the stick
		rsync --progress <whatever>.iso /mnt/isostick/boot/iso
	8. Create the corresponding menuentry
        some of the usual ones can already be found in the grub.cfg
	9. Unmount and enjoy

If you have additional configurations, please file a pull request for them.
