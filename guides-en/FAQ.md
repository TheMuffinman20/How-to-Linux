# FAQ

### Why does my USB stick not appear in the boot menu?

Check whether the USB stick was flashed correctly, whether it is connected, and whether the BIOS/UEFI supports the correct boot medium. Sometimes you have to select the USB stick manually as a boot option in the BIOS/UEFI.

### How do I know if my computer uses UEFI or BIOS?

You can usually check this in the BIOS/UEFI settings. UEFI is the newer standard and is usually labeled as “UEFI”. BIOS is the older standard. If you see the USB stick listed as “UEFI” in the boot menu, you are probably using UEFI.

### What if BitLocker prevents me from booting Linux?

Disable BitLocker from Windows. Also keep the recovery key from your Microsoft account available in case you no longer know the code.

### What if the installer does not detect Windows?

Check whether you have created enough free space. If not, free up space in Windows first. If the installer still does not detect an existing Windows installation, you can configure the partitions manually.

### How do I choose the right partition layout?

For dual-boot, the usual choice is: Linux alongside Windows. For a fresh installation without Windows, you often choose “Erase disk and install Linux”.

### What if I want to reinstall Windows later?

Then you will need to reconfigure the Linux bootloader or reinstall the Windows installation. The order matters: if you are using dual-boot, it is usually best to install Windows first and Linux second.

### Is Secure Boot always required to be disabled?

No, not for every distribution. Only disable Secure Boot if the documentation of your chosen distro says to, or if the system will not boot otherwise.

### What if I want to remove Linux later?

That depends on how you installed it. If you are using dual-boot, you can later delete the Linux partition and return the free space to Windows. In some cases, you must also reconfigure the bootloader.

> [!NOTE]
> For other questions, you can visit the IT Lab, where students and lecturers are ready to help you as quickly and effectively as possible with problems. Feel free to stop by!