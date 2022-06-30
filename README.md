# TEV-JetsonXavier-NX_pinmux
The Jetson Xavier-NX pinmux file, for JetsonXavier-NX TN-TEK 3/8 series.

### Folder location(created by TEV-Jetson_Jetpack_script)
```
<nvidia_folder>/Linux_for_Tegra/sources/TEK3-NVJETSON_Xavier-NX_pinmux
```

&nbsp;

### Create pinmux file
Edit **Jetson_Xavier_NX_Pinmux_Configuration_Template_v1.06.xlsm** under windows environment.
Click On the **macro**(Generate DT file) on top of the xlsm. 

![image](https://user-images.githubusercontent.com/83322668/176626118-381a21d3-b126-46c8-830d-8f53ce22600a.png)

Click OK

![image](https://user-images.githubusercontent.com/83322668/176626422-6fe8cbb8-4018-499b-96a8-68c239bd0eba.png)

Type the \<name> twice. (For example: tek3)

![image](https://user-images.githubusercontent.com/83322668/176626516-96205bce-12a1-4061-824a-12f70f11cfb4.png)

You will see the result

![image](https://user-images.githubusercontent.com/83322668/176626603-5465cbcd-986e-4093-bb1c-05c16736c5bd.png)

### Generate pinmux cfg (For example: tek3)
```coffeescript
# Copy files to script location
$ cp -rv tegra19x-tek3-pinmux.dtsi <nvidia_folder>/Linux_for_Tegra/kernel/pinmux/t19x/
$ cp -rv tegra19x-tek3-gpio-default.dtsi <nvidia_folder>/Linux_for_Tegra/kernel/pinmux/t19x/
$ cp -rv tegra19x-tek3-padvoltage-default.dtsi <nvidia_folder>/Linux_for_Tegra/kernel/pinmux/t19x/

# Generation cfg file
$ cd <nvidia_folder>/Linux_for_Tegra/kernel/pinmux/t19x/
$ python pinmux-dts2cfg.py --pinmux addr_info.txt gpio_addr_info.txt por_val.txt    \
                tegra19x-tek3-pinmux.dtsi tegra19x-tek3-gpio-default.dtsi \
                1.0 > TEST_tegra19x-mb1-pinmux-p3668-a01.cfg
```
### Copy pinmux cfg file and flash into device
```coffeescript
# Copy cfg files
$ sudo cp -rp TEST_tegra19x-mb1-pinmux-p3668-a01.cfg \
                <nvidia_folder>/Linux_for_Tegra/bootloader/t186ref/BCT/tegra19x-mb1-pinmux-p3668-a01.cfg

# flash into device
$ cd <nvidia_folder>/Linux_for_Tegra
$ sudo ./flash.sh -k MB1_BCT jetson-xavier-nx-devkit-emmc mmcblk0p1

```
