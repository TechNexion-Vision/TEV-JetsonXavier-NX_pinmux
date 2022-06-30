# TEV-JetsonXavier-NX_pinmux
The Jetson Xavier-NX pinmux file, for JetsonXavier-NX TN-TEK 3/8 series.

### Folder location(created by TEV-Jetson_Jetpack_script)
```
<nvidia_folder>/Linux_for_Tegra/sources/TEK3-NVJETSON_Xavier-NX_pinmux
```

&nbsp;

### Create pinmux file
Edit **Jetson_Xavier_NX_Pinmux_Configuration_Template_v1.06.xlsm** under windows environment.


### Copy files to device-tree location(For example: TEK3-NVJETSON)
Copy **tegra210-tek3-gpio-default.dtsi**
to 
```
<nvidia_folder>/Linux_for_Tegra/sources/hardware/nvidia/platform/t210/porg/kernel-dts/porg-platforms/tegra210-tek3-nvjetson-a1-gpio-default.dtsi
```
Copy **tegra210-tek3-pinmux.dtsi**
to 
```
<nvidia_folder>/Linux_for_Tegra/sources/hardware/nvidia/platform/t210/porg/kernel-dts/porg-platforms/tegra210-tek3-nvjetson-a1-pinmux.dtsi
```

### Take effect
Just re-compile the kernel/ device-tree.
``` coffeescript
$ cd <nvidia_folder>/Linux_for_Tegra/sources/kernel/kernel-4.9/
$ ./compile_kernel.sh
```

* Copy new device-tree to device

Copy **Linux_for_Tegra/sources/kernel/kernel-4.9/arch/arm64/boot/dts/tegra210-tek3-nvjetson-a1.dtb**

to device 
```
/boot/
```
&nbsp;

* Copy new device-tree to workspace, create new system.img and flash.

Copy **Linux_for_Tegra/sources/kernel/kernel-4.9/arch/arm64/boot/dts/tegra210-tek3-nvjetson-a1.dtb**

to 
```
<nvidia_folder>/Linux_for_Tegra/rootfs/boot/
```
```coffeescript
$ sudo ./flash.sh jetson-nano-devkit-emmc mmcblk0p1 
```
