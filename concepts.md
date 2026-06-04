# Concepts learned

## General

### OS
An OS is the bridge between the user and the hardware. The operating system is responsible for managing the resources the bare metal gives.

### Kernel
The spefic part of your OS which manages the resources and interacts with the hardware is called kernel. It manages the memory, schedules task, determines priority of the things being used.

### Shell
The shell is the interpreter of the language chosen to be interacted with for the user interface called terminal. The shell recieves the commands and translates it to machine code so the kernel can understand it.

### Firmware
The firmware is responsible for initializing each component and for checking the status of the component. The firmware is stored in ROM memory, which for its purpose to be kept for a long time, and rewritten sometimes. 

### Bootloader
Bootloader or bootstrap is responsible for loading the kernel(vmlinuz) and the initramfs.img to the memory and afterwards giving control to the kernel.
