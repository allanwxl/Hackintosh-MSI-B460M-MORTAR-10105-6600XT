## 硬件配置

| 配置 | 型号 | 价格 | 渠道 |
| ---- | ---- | --- | --- | 
| CPU | Intel i3 10105 | 665 | 黄鱼 |
| 主板 | 微星 MSI MAG B460M MORTAR WIFI | 400 | 黄鱼 |
| 显卡 | 撼讯红魔 RX 6600XT 8G | 1388 | 黄鱼 |
| 内存 | 美商海盗船(复仇者LPX系列) 3000MHz 16G * 2 | 450 | 黄鱼 |
| SSD1 | 京东京造 512GB麒麟系列SSD固态硬盘 M.2接口（NVMe协议）PCIe3.0四通道 300TBW | 234 | 京东自营 |
| SSD2 | 斯加特（Asgard）1TB AN系列-游戏极速版｜五年质保 windows | 799 | 京东自营 |
| 机箱 | 乔思伯 D30 | 280 | 黄鱼 |
| 电源 | 酷冷至尊(CoolerMaster)GX850W电源 电脑电源/金牌全模组/日系主电容/支持双CPU | 609 | 京东自营 |
| CPU 风扇 | 利民 Forzen Magic 240 Argb | 270 | 黄鱼 |
| 机箱风扇 | 棱镜 * 5 | 150 | 黄鱼 |
| WiFi + 蓝牙 |  BCM94360CD | 160 | 黄鱼 |

## 年轻人的第一台黑苹果 目前版本 `0.9.3` `Ventura 13.3.1`
### 经费有限, 主要配件来自于小黄鱼, 已婚人士, 钱不由己, 后期优先更换CPU, 总计 5405 元。
### 之前小黄鱼跟机箱一起收的450w电源 因为加了独显 在做压力测试的时候炸了 建议这套配置使用650w电源。
### 条件允许建议直接6700XT 目前已经降到1500左右。
### 之前用过QTB1 10900es的U 主板总是报故障灯 每次插拔内存才有几率进入系统 建议跟我一样脸黑的同学不要尝试
### 已经入手M1 RPO MacBook 黑苹果用于临时在家解决公司问题。

### 功能（完善度99%）
- cpu支持睿频
- 支持睡眠/唤醒
- 所有USB端口定制
- 核显硬件加速
- 板载声卡
- 板载网卡
- 各种CPU、GPU传感器齐全
- 一键重置nvram (空格）
- 双系统记忆启动（ctrl+回车)

### EFI下载与使用
[下载链接](https://github.com/allanwxl/Hackintosh-MSI-B460M-MORTAR-10105-6600XT/releases)，替换`EFI`-`Boot` 下的文件，和`EFI`下添加`OC`文件夹


### CPU支持
- 理论支持所有10代CPU

### 显卡支持
- 支持仅有核显的UHD630显卡
- 支持 5000~6000 系显卡，且不需要改动设置
- 5000 系列以下的显卡，或许需要自行探索一番
- 支持AMD独显 RX 5500/5600/5700 系列显卡(需使用config.plist)
> PS: 使用独显的需在BIOS里强制打开CPU核显（高级 -> 内建显示配置 -> 集成显卡多显示器(IGD Multi-monitor) -> 允许），否则核显硬件解码失效，只使用核显的可以忽略


### BIOS设置
#### 开启D.T.M 剩下不用管
* 安全启动：关闭
* USB设备从S3/S4/S5唤醒：允许
* PS/2鼠标从S3/S4/S5唤醒：允许
* USB键盘从S3/S4/S5唤醒：任意键
* 集成显卡多显示器：允许（否则核显硬件解码失效，只使用核显的可以忽略）
* OC -> CPU 特征 -> Intel 虚拟化技术：允许
* OC -> CPU 特征 -> Intel VT-D 技术：禁止
* OC -> CPU 特征 -> CFG锁定：禁止


### 系统安装
* 我使用的独行秀才 提供的官方镜像 https://mp.weixin.qq.com/s/yK0R0QGw4fguQgrgfzRiNw

* 若安装镜像卡加号或其它异常无法安装，可使用本EFI替换安装镜像的EFI进行尝试
(本EFI请使用config_install.plist配置文件，即删除原config.plist后重命名config_install.plist为config.plist即可)

* 系统安装成功后，替换为本EFI默认的config.plist文件即可


### 板载网卡设置
* 系统偏好设置 -> 网络 -> 以太网（高级） -> 硬件 -> 配置:手动, 速度:100baseTX(千兆网络环境可选择1000baseT), 双工:全双工, MTU:标准1500

### 无线网卡和蓝牙设置
* 如果是 Intel 无线网卡，可以不修改Kernel-add
* 如果是 博通 无线网卡，在 Kernel-add 删除或者Enabled:false，带有intel字样的项目，同时开启4个带有 brcm 相关的选项驱动补丁
* `使用博通无线网卡需要USB定制 我是在window下使用USBToolBox 这个来做的 具体使用请看官网`
* `板载的无线网卡一定要拆除哈 否则跟pcie的无线网卡冲突 识别不了`

### 关于睡眠的问题
* BIOS默认关闭了USB唤醒，睡眠后需按电源键唤醒
* 需鼠标键盘唤醒的，在BIOS里设置USB唤醒为允许即可
> PS: 若睡眠有问题的可使用 Hackintool 工具，切换到电源选项，点击下面的螺丝刀图标修复

### 关于Mac序列号的问题
* 下载 OpenCore Configurator for Mac，打开 PlatformInfo -> Model Lookup | Check Coverage 右侧选择 iMac20,1 机型（生成你的唯一硬件UUID），然后 Save as (另存为) config.plist
* 在config.plist文件中找到如下代码，记录MLB、SystemSerialNumber和SystemUUID的值并记住它，更新EFI时，用你记录的值替换 /OC/config.plist 下对应的值即可
> PS: 还可使用 Hackintool 工具（系统 -> 序列号生成器）来获取三码

```
<key>PlatformInfo</key>
<dict>
    <key>Generic</key>
    <dict>
        <key>AdviseWindows</key>
        <false/>
        <key>MLB</key>
        <string>C02047501CDPHCDAD</string>
        <key>ProcessorType</key>
        <integer>4105</integer>
        <key>ROM</key>
        <data>ESIzRFVm</data>
        <key>SpoofVendor</key>
        <true/>
        <key>SystemMemoryStatus</key>
        <string>Auto</string>
        <key>SystemProductName</key>
        <string>iMac20,1</string>
        <key>SystemSerialNumber</key>
        <string>C02DQSZFPN5T</string>
        <key>SystemUUID</key>
        <string>C567A1A9-9233-4D4D-B021-E1F38B112F33</string>
    </dict>
```

### Win+Mac双系统解决Win系统时间时差问题
* 在Windows下运行
```
Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_DWORD /d 1
```

### 设置默认启动项
* 在启动选择界面，先选中要启动的项，然后按键盘的 Ctrl + Enter (回车键) 进入系统，下次重启后默认就选中该项了

### 所知问题（持续更新中）
- 安装
    - 推荐使用黑果小兵的clover 或者 oc 安装
- efi问题
    - 理论支持所有10代CPU，如果无法使用，可以尝试删除`NVRAM`-`Add`-`7C436110-AB2A-4BBB-A880-FE41995C9F82`-`boot-args` 里面的参数
    - RX 5000 和 6000 系列，一定要`boot-args`中添加 `agdpmod=pikera`，否则黑屏（不是我说的，文档写的）
- 希望接收到系统更新的 请打开 Misc - Security - SecureBootModel= Default

## <a id="use">使用角色</a>
- $\color{red} {[迫击炮b460m]}  + \color{blue} {[Intel 10代CPU]} + \color{orange}{[AMD 5000~6000 系显卡]} + \color{pink}{[Intel 无线网卡与蓝牙]}$，删 `Kernel`-`add` 中 所有相关 Brcm 选项的项目，同时勾选 Intel 相关选项的 Enabled = true
- $\color{red} {[迫击炮b460m]} +  \color{blue} {[Intel 10代CPU]} + \color{orange}{[AMD 5000~6000 系显卡]} + \color{pink}{[BCM 无线网卡与蓝牙（非白卡）]}$，删 `Kernel`-`add` 中 所有相关Intel选项的项目，同时勾选Brcm相关选项的 Enabled = true
- $\color{red} {[迫击炮b460m]} +  \color{blue} {[Intel 10代CPU]} + \color{orange}{[AMD 5000~6000 系显卡]} + \color{pink}{[BCM 白卡]}$，删 `Kernel`-`add` 中 所有相关蓝牙WiFi驱动选项，或者Enabled = false，或啥都不做
- $\color{red} {[迫击炮b460m]} +  \color{blue} {[Intel 10代CPU]} + \color{orange}{[核显]}$，删完`NVRAM`-`Add`-`7C436110-AB2A-4BBB-A880-FE41995C9F82`-`boot-args`里的参数
- $\color{red} {[迫击炮b460m]} +  \color{blue} {[Intel 10代CPU]} + \color{orange}{[不带核显]}$，删 `DeviceProperties`-`add`-`PciRoot(0x0)/Pci(0x2,0x0)`-`AAPL,ig-platform-id`

## 进阶指南
- 白卡可以解决很多问题，实现完美。
- OC的作者更新非常频繁，可能上个版本能用的config.plist，下个版本就挂了，因为其中的字段变了

## 感谢
- 感谢 国光的黑苹果安装教程 https://apple.sqlsec.com/
- 引用 https://github.com/leggod/B460M-MORTAR-Hackintosh