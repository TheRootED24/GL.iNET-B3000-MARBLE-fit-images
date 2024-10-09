# GL.iNET-B3000-MARBLE-fit-images
Vanila Openwrt fit images for the GL.iNET B3000

It comes with the usual caveat, use at your own risk !!
Serial connection is required for flashing, see instructions below
A final warning ... use at your own risk 

# Setup  
setup tftp server with ip 192.168.1.1 \
put the openwrt-qualcommax-ipq50xx-glinet_gl-b3000-squashfs-nand-factory.ubi file into root of tftp server

# Flashing
1. power up router with serial console open to see boot log
2. press "gl" when prompted by uboot
3. enter the following cmds ...
 
 ## SET ROUTER IP
setenv ipaddr 192.168.1.2

## SET TFTP SERVER 
setenv serverip 192.168.1.1

## Upload the firmware to the RAM from tftp server
tftpboot openwrt-qualcommax-ipq50xx-glinet_gl-b3000-squashfs-nand-factory.ubi

## Flash firmware to system 0
flash rootfs \
setenv flag_try_sys1_failed 0 \
setenv flag_boot_rootfs 0 \
setenv flag_last_success 0

## Save everything
saveenv

## Reboot it to openwrt 
reset
