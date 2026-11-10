# How do I choose the right bootloader?

This guide helps you choose a suitable bootloader for your Linux installation. The bootloader starts before the operating system loads and is used to select which operating system to boot, such as Linux or Windows. You cannot download this system like a program: you have to make the choice during installation.

The best choice depends mainly on your firmware (the built-in software on your computer that controls the hardware and determines how the system boots) and the number of operating systems (only Linux or Linux alongside Windows), but also on how much you want to customize.

> [!IMPORTANT]
> First, check whether your computer boots in **UEFI mode** or the older **BIOS/Legacy mode** by checking the **BIOS**. For modern computers and a dual-boot setup with Windows, **UEFI** is usually the preferred choice.

### 1. Consistency

The bootloader must remain reliable and start the correct operating system without surprises.

- Does the bootloader work well with your Linux distribution?
- Can it automatically detect Windows?
- Does the boot menu continue to work after a kernel or system update?

### 2. Flexibility

A bootloader can be simple, but it can also offer many options for themes, recovery tools, and multiple kernels.

- Do you want to boot only Linux, or also Windows and other systems?
- Do you want to configure boot options and themes yourself?
- Do you need support for multiple Linux kernels?

### 3. Compatibility

The bootloader must match the firmware and disk layout of your computer.

- **UEFI** uses an EFI system partition, usually formatted as FAT32.
- **BIOS/Legacy** uses a different boot method and is less suitable for a new dual-boot installation.

> [!NOTE]
> Install Linux and the bootloader in the same mode.
> Start the Linux USB from the option that begins with **UEFI** as well.

## Types of bootloaders

### GNU GRUB

<img src="../../images/Bootloaders/GRUB_logo.png" alt="GRUB" width="100">

**GRUB** is the most widely used and best-supported choice.

- Suitable for dual-boot with Windows
- Works with both UEFI and BIOS/Legacy
- Lots of documentation and support available
- More configuration and a more complex default setup

Choose GRUB if compatibility and broad support are your main priorities.

> [!IMPORTANT]
> **GRUB** cannot be used if the **EFI** partitions are not on the same disk, because they cannot be found.

### systemd-boot

<img src="../../images/Bootloaders/Systemd-boot_logo.png" alt="Systemd-boot" width="100">

systemd-boot is a lightweight bootloader for modern UEFI systems.

- Simple and fast
- Works well for a Linux-only installation
- Requires little configuration
- Not intended for BIOS/Legacy
- Less suitable when you want many different systems to be managed automatically

Choose systemd-boot if you have a modern UEFI computer and want a simple Linux installation.

### Limine

<img src="../../images/Bootloaders/Limine_logo.png" alt="Limine" width="100">

Limine is a modern bootloader with support for both UEFI and BIOS/Legacy.

- Clear and modern boot menu
- Suitable for Linux and Windows in a dual-boot setup
- Plenty of features without making the basic configuration complicated
- Less commonly included in distributions than GRUB

> [!NOTE]
> In this workshop, we choose **Limine**, because it is a modern and flexible choice for a system with Linux and possibly Windows.

### rEFInd

<img src="../../images/Bootloaders/rEFInd_logo.png" alt="rEFInd" width="150">

rEFInd shows the available operating systems as clear boot options.

- Useful when you use multiple operating systems
- Visually clear menu
- Primarily aimed at UEFI
- May require extra configuration in unusual installations

Choose rEFInd if you use several UEFI operating systems side by side and value a visual menu.

## Best choice

### Windows and Linux (dual-boot)

Choose **Limine** or **GRUB**.

- Limine if you want a modern and clear menu.
- GRUB if you want maximum compatibility and documentation.

### Linux only (single-boot)

Choose **systemd-boot** or **Limine**.

- systemd-boot for a simple UEFI installation.
- Limine when you want more customization options.
- GRUB remains a safe choice if your distribution provides it.

### Multiple Linux installations

Choose **GRUB**, **Limine**, or **rEFInd**.

- These bootloaders make it easier to manage multiple systems or kernels in one boot menu.

### Older hardware

Choose **GRUB**.

- A very lightweight bootloader that does not make older computers or hardware difficult to use.

### Recommended choice

For this workshop:

- Use **UEFI** if your computer supports it.
- Choose **Limine** for a modern dual-boot or a flexible Linux installation.
- Use an **FAT32 EFI system partition** for the boot files.
- Always make a backup before changing partitions or boot settings.

> [!WARNING]
> A wrong bootloader choice does not normally delete your files automatically, but a wrong partition or firmware setting can prevent an operating system from booting. Therefore, check the disk, boot mode, and EFI partition carefully before confirming the installation.
