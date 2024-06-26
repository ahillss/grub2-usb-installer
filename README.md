# Bootable USB

Instructions and a grub2 config file for booting linux installers. live disks and a windows 7 installer.

## Making it bootable

1. Use fdisk to create a single partition (of FAT32) and set the bootable flag.

2. Format it: ```mkfs.msdos -nMYINST -F 32 /dev/sda1``` (replace sda1 with your partition)

3. Mount the partition.

4. Install grub2 onto it: ```grub-install --no-floppy --root-directory=/where/it/is/mounted /dev/sda``` (replace sda with your device)

5. Add your grub.cfg to yourusbdriveroot/boot/grub/

## Making it bootable with UEFI

1. follow the original 1-3 steps above

2. grub-install --target=x86_64-efi --removable --efi-directory=/where/it/is/mounted --boot-directory=/where/it/is/mounted

3. Add your grub.cfg to yourusbdriveroot/grub/

4. TODO, unable to boot images? 

## Removing boot section

Warning: This deletes the partition table.

```dd if=/dev/zero of=/dev/sda bs=512 count=1```

## Making a Windows 7 installer

Open the windows 7/10 iso and extract all the files directly onto the usb.


## Boot entry examples

View the [grub.cfg](grub.cfg) for examples on booting different installs, disks etc.
