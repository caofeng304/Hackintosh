我的Hackinktosh配置信息

主板： Gigabyte X99 SOC Champion
CPU:  E5-2696V4
显卡：	MSI GTX 1080 Ti (MS-V360)
内存： 4x16G DDR4  2666Mhz
无线网卡&蓝牙：T919黑苹果免驱BCM943602C
硬盘： 无所谓


上传了两份EFI文件

其中“ EFI_Wifi not fixed, For StartupUse(进入系统可使用OCLP安装显卡驱动）”  建议在启动安装的时候使用该EFI，系统安装完成后使用 OpenCore Legacy Patcher 安装显卡及无线网卡驱动补丁
https://dortania.github.io/OpenCore-Legacy-Patcher/


补丁打完后可以使用“EFI_Wifi fixed” EFI





这两个EFI主要区别在启用的Kexts数量不同  （EFI_Wifi fixed下增加了无线网卡的kext）， 另外就是启动时的boot-args不同

其中“ EFI_Wifi not fixed, For StartupUse(进入系统可使用OCLP安装显卡驱动）”EFI启动时的boot-args是：

-v debug=0x100 -no_compat_check  npci=0x3000 amfi_get_out_of_my_way=0x1 ngfxcompat=1 ngfxgl=1 nvda_drv_vrl=1 （这个启动后进入系统可以使用 OpenCore Legacy Patcher 打补丁，否则 OpenCore Legacy Patcher 会报一些错误）


![image](https://github.com/user-attachments/assets/c2b5b418-d468-4ac3-9ecc-5d80a841fc04)



“EFI_Wifi fixed” EFI 启动时的boot-args是：

-v debug=0x100 -no_compat_check  npci=0x3000  ngfxcompat=1 ngfxgl=1 nvda_drv_vrl=1 amfi=0x80 revpatch=sbvmm ipc_control_port_options=0   （是对增加的无线网卡kext的支持）

![image](https://github.com/user-attachments/assets/993892ab-85f9-48a1-8c05-ba2a46b1a184)
