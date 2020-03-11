# Bootable USB

Instructions and a grub2 config file for booting linux installers. live disks and a windows 7 installer.

## Making it bootable

1. Use fdisk to create a single partition (of FAT32) and set the bootable flag.

2. Format it: ```mkfs.msdos -nMYINST -F 32 /dev/sda1``` (replace sda1 with your partition)

3. Mount the partition.

4. Install grub2 onto it: ```grub-install --no-floppy --root-directory=/where/it/is/mounted /dev/sda``` (replace sda with your device)

## Removing boot section

Warning: This deletes the partition table.

```dd if=/dev/zero of=/dev/sda bs=512 count=1```

## Making a Windows 7 installer

Open the windows 7/10 iso and extract all the files directly onto the usb.


## Boot entry examples

View the [grub.conf](grub.conf) for examples on booting different installs, disks etc.
