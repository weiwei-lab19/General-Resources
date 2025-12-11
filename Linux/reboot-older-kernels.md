# Reboot Older Kernels
This is a guide on how to fix a bad update in your linux kernel that messes with the functionality of the operating system.
My Linux kernel for my Ubuntu operating system updated itself automatically in order to fix a system error. After the update and restarting the computer, a lot of things did not work. For example, I couldn't connect to wifi, the mouse track pad didn't work, the touch screen on my ASUS computer did not respond, and my display settings were not right.

The method to fix this is by going back to a previous linux kernel that didn't have these problems before the update. 

This was done on (12/11/2025): 
- OS: Ubuntu 25.04
- Firmware Version: N501VW.304
- Hardware Model: ASUSTeK COMPUTER INC.N501W
- Processor: Intel® Core™ i7-6700HQ × 8 

The bad updated kernel was Linux 6.14.0-37-generic, we want to revert to an older kernel that worked which was Linux 6.14.0.36-generic. 
1) Restart your PC
2) Enter the Ubuntu GRUB menu by pressing and holding the `SHIFT` key during the start-up screen of your computer.
3) Select `Advanced options for Ubuntu`.
4) From the list of kernels, select the kernel you wish to boot up.
    - In this case, since we want to boot up the older kernel before the update, we pick `Linux 6.14.0.36-generic`
    - **Don't** pick the `recovery mode` option of the kernel, I found that this version had some bugs related to it, like not detecting monitors that I've connected to the PC.
5) After booting the older kernel, remove the bad kernel with
    ```bash
    sudo apt-get purge linux-image-6.14.0-37-generic
    ```
If you don't know which kernel is the bad kernel, you can always restart and switch between different kernels in the GRUB menu to test it out.
