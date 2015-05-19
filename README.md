# The Boot Process

Now, we begin our journey.
When we reboot our computer, it must start up again, initially without any notion of an operating system. Somehow, it must load the operating system --- whatever variant that may be --- from some permanent storage device that is currently attached to the
computer (e.g. a  floppy disk, a hard disk, a USB dongle, etc.).

As we will shortly discover, the pre-OS environment of your computer offers little in the way of rich services: at this stage even a simple file system would be a luxury (e.g. read and write logical files to a disk), but we have none of that. Luckily, what we do have
is the Basic Input/Output Software (BIOS), a collection of software routines that are initially loaded from a chip into memory and initialised when the computer is switched on. BIOS provides auto-detection and basic control of your computer's essential devices, such as the screen, keyboard, and hard disks.

After BIOS completes some low-level tests of the hardware, particularly whether or not the installed memory is working correctly, it must boot the operating system stored on one of your devices. Here, we are reminded, though, that BIOS cannot simply load a
file that represents your operating system from a disk, since BIOS has no notion of a file-system. BIOS must read specific sectors of data (usually 512 bytes in size) from specific physical locations of the disk devices, such as Cylinder 2, Head 3, Sector 5 (details of disk addressing are described later).

So, the easiest place for BIOS to find our OS is in the first sector of one of the disks (i.e. Cylinder 0, Head 0, Sector 0), known as the boot sector. Since some of our disks may not contain an operating systems (they may simply be connected for additional storage), then it is important that BIOS can determine whether the boot sector of a particular disk is boot code that is intended for execution or simply data. Note that the CPU does not differentiate between code and data: both can be interpreted as CPU instructions, where code is simply instructions that have been crafted by a programmer into some useful algorithm.

Again, an unsophisticated means is adopted here by BIOS, whereby the last two bytes of an intended boot sector must be set to the magic number 0xaa55. So, BIOS
loops through each storage device (e.g. floppy drive, hard disk, CD drive, etc.), reads the boot sector into memory, and instructs the CPU to begin executing the first boot sector it finds that ends with the magic number.

This is where we seize control of the computer.
