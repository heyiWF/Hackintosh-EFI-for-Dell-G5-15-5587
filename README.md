# Hackintosh EFI for Dell G5 15 5587

适用于Dell G5 5587的Hackintosh Clover EFI文件，由[@Sosueyakiko的EFI](https://github.com/Sosueyakiko/Clover_EFI-For-DELL-G5-5587)精简而来。

+ 移除了无关的kexts

+ `config.plist`优化，启用修复关机（貌似没什么用）

+ 加入了`VoodooI2C`作为键盘和触控板驱动，替换原有的PS2驱动（因为这机子本身就是I2C的HID设备，PS2也能用但是触控板手势相当怪异）

+ 机型设置成了`MacBookPro15,3`，介意的同学可以设置回`MacBookPro15,1`

## 目前存在的问题

+ 声卡驱动不完美，你能且只能在**开机前**决定要使用扬声器还是耳机：插入耳机会导致识别不到内建扬声器，只能用耳机听；不插耳机开机后扬声器正常，但耳机孔失效。想切换输出设备的，请重启，并在启动前拔出/插入设备。

+ 系统里识别到两个音频设备，很奇怪。插耳机，第一个设备有声音，第二个设备没声音；用内建扬声器，反之。

+ Thunderbolt 3接口（实际上只能达到USB 3.2 Gen 1（未测试）），如果要连接外部存储设备，需要在**开机前**连接，否则不识别。如果要连接视频输出设备，需要在**开机后**连接，否则无法开机（未测试）。音频输出设备连接此端口无效。

+ 关机不断电。可能是我主板问题，修好了我再测试一下。

+ ACPI/patched目录下的SSDT-EC.aml似乎并没有启用，需要在Clover Configurator中勾选Drop OEM？

+ HDMI接口和内建读卡器失效（未测试），独立显卡无法使用。这个不解释。
