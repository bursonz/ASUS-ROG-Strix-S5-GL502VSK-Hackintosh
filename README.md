# ASUS-ROG-Strix-S5-GL502VSK-Hackintosh
华硕玩家国度StrixS5（GL502VSK）黑苹果EFI（10.13.6）
作者：[Burson](faineant.cn)

## 说明

EFI的OCplist配置文件名中已详细标记使用情况，将其重命名为`config.plist`即可使用。其中所用到的部分工具放在`tools`中，大部分ACPI、Driver和Kext原包也放在了`lib`中，可以参考包名的版本信息进行更新或者回滚。

如需使用，请参考以下几点建议：

- 有动手能力的请选用`config5_不可用_优化版本.plist`作为起步配置，然后对照可用版本进行修改，以达到良好的使用效果，反之亦可
- 随机生成对应机型的三码，并到苹果官网查询序列号是否存在（不存在即可用），请不要直接使用文件的信息，以保证数据安全。
- 如遇到进不去BIOS、进BIOS卡黑屏等启动项异常，请使用u盘引导OC，并在OC中使用`reset NVRAM`重置NVRAM即可。
- 本人在使用过程中，因系统版本问题（17G66）并没有成功驱动N卡正常工作，且其它设备（触摸板、背光等）也有部分问题，但在最后修改过的plist中已包含kext解决方案。因个人时间关系暂时没有继续学习解决，如果有人调试成功希望可以提交commit与本人分享。

## 机型信息

ASUS-ROG-Stirx-S5-GL502V-SK

| 名称      | 型号                                    | 备注                      |
| --------- | --------------------------------------- | ------------------------- |
| 处理器    | Intel core i7 7700HQ                    | 隶属于Kaby Lake           |
| 芯片组    | Intel HM175                             |                           |
| 内存      | 2*8GB 2400MHz Samsung M471A1K43CB1-CRC  |                           |
| 显卡      | Nvidia GTX 1070 Mobile (Asus)           | 该机型无集显，系硬件屏蔽  |
| 硬盘      | 三星960PRO 512GB + TOSHIBA MQ01ABD100   | 原厂固态为海力士128GB     |
| BIOS      | AMI GL502VSK.309                        |                           |
| 声卡      | Realtek ALC255                          | layoutid可能是13 (未验证) |
| 摄像头    | USB2.0 HD UVC WebCam                    | 免驱 (未验证)             |
| 有线网卡  | Realtek RTL8168                         | 8168与8111同系列          |
| 无线网卡  | Intel AX200                             | 原厂为 Intel AC8260       |
| 键盘      | ROG MacroKey                            | 走集成的USB控制器         |
| 触摸板    | Elan 1200 I2C HID                       | Asus定制                  |
| USB控制器 | ASMedia ASM1142 USB 3.1 xHCI Controller | 对应type c接口            |

## 参考链接

> 以下为部分自用链接，有精力会继续更新。

- OpenCore
  - [OpenCore入门配置详解](http://imacos.top/2020/04/04/1616/)
  - [Kaby Lake平台OpenCore 引导config.plist配置](http://imacos.top/2020/04/14/2151/)
  - [macOS 启动参数列表](https://blog.skk.moe/post/macos-boot-args/)
  - [OpenCore兼容的kext驱动整理速查表](https://www.mfpud.com/topics/1246/)
- 故障排疑
  - [macOS 10.13安装中常见的问题及解决方法](https://blog.daliansky.net/macOS-10.13-installation-of-common-problems-and-solutions.html)【黑果小兵】
  - [OpenCore引导-v各种卡及OC引导常见问题解决方案速查表合集](http://imacos.top/2021/01/19/0154/)
- 完善优化
  - [安装完黑苹果系统之后一般要做的事](https://www.mfpud.com/topics/1177/)
  - DSDT
    - [OpenCore引导各平台所需要的SSDT](http://imacos.top/2020/03/29/ssdt/)
  - CPU与SMC
    - [AsusSMC-1.4.1.kext](http://imacos.top/2021/03/17/asussmc-kext/)
  - 显卡
    - [WebDriver-387.10.10.10.40.140 黑苹果N卡显卡驱动支持10.13.6 合集 - 黑苹果社区](https://osx.cx/webdriver-nv-10-13-6.html)
    - [WebDriver-387.10.10.10.40.130 支持10.13.6 (17G8030)](https://blog.csdn.net/xinlignduyu/article/details/107114671)
    - [N卡WebDriver合辑](http://imacos.top/2019/08/19/nvidia/)
    - [针对MAC家族的CUDA驱动 - NVIDIA CUDA FOR MACOS RELEASE-黑苹果动力](https://www.mfpud.com/topics/107/) CUDA Driver
    - [英伟达显卡黑苹果驱动 macOS 10.13.6 High Sierra NVIDIA web Drivers-黑苹果动力](https://www.mfpud.com/topics/105/)
  - 声卡
    - [AppleALC.kext声卡驱动支持的硬件型号与ID速查表](http://imacos.top/2019/09/07/1920/)
    - [黑苹果OC引导注入声卡ID教程，解决开机无声音等问题](https://blog.csdn.net/iCanCode/article/details/108238079)
    - [使用AppleALC声卡仿冒驱动AppleHDA的正确姿势 | 黑果小兵的部落阁](https://blog.daliansky.net/Use-AppleALC-sound-card-to-drive-the-correct-posture-of-AppleHDA.html)
  - 网卡
  - IO设备
    - [USBInjectAll-0.7.5.kext](http://imacos.top/2019/09/02/0859/)
  - 
  - Fixup
    - 休眠唤醒
      - [HibernationFixup-1.3.9.kext](http://imacos.top/2019/09/16/hibernationfixup-kext/)
      - [EnableLidWake-2.1.kext](http://imacos.top/2021/03/18/enablelidwake-kext/)
    - 显示
      - [NightShiftUnlocker-2.2.1.kext](http://imacos.top/2021/03/20/nightshiftunlocker-2-2-1-kext/)
    - 传感器
      - [NoTouchID-1.0.3.kext](http://imacos.top/2019/09/16/notouchid-kext/)
    - 内存
      - [acidanthera/RTCMemoryFixup](https://github.com/acidanthera/RTCMemoryFixup)
      - [RTCMemoryFixup-1.0.7.kext](http://imacos.top/2020/03/31/rtcmemoryfixup-kext/)
      - [SystemProfilerMemoryFixup-1.0.0.kext](http://imacos.top/2020/03/13/systemprofilermemoryfixup-kext/) 关于本机不显示内存信息
    - 软件
      - [Shiki-2.2.7.kext](http://imacos.top/2020/11/24/shiki-kext/) 打开iTunes后报错闪退
- 参考机型
  - [ASUS-GL503GE-Hackintosh-master](https://github.com/Bimoaryo5/ASUS-GL503GE-Hackintosh-master)
  - [华硕GL502VM/S5VM10.12.5接近完美&工具一站式下载6700hq+alc255+elan](http://bbs.pcbeta.com/viewthread-1750224-1-1.html)
  - [Hackintosh黑苹果长期维护机型整理清单](https://blog.daliansky.net/Hackintosh-long-term-maintenance-model-checklist.html)
- 系统镜像
  - macOS 10.15 Catalina
    - [10.15.5 (19F96) Clover 5118](https://www.winos.vip/843.html)
    - [10.15db2 (19A487) Clover 4964](https://www.seoxiehui.cn/article-142317-1.html)
    - [10.15db2 (19A487) Clover 4964](https://www.cnblogs.com/happy5858/p/11509911.html)
  - 10.13 High Sirrea
    - [10.13.6 (17G2112) 特别版 Clover 4606](https://blog.daliansky.net/macOS-High-Sierra-10.13.6-17G2112-Release-Special-with-Clover-4606-original-mirror.html)【黑果小兵】
    - [10.13.6 (17G65) Clover 2.4k r4596](https://imac.hk/macos-high-sierra-10-13-6-17g65.html)
- 其他教程
  - [黑苹果 MacOS 10.15 Catalina 安装详细教程带工具资料](https://blog.csdn.net/qq_28735663/article/details/99695786)

## 特别链接(GitHub repos)
> (部分)使用到的工具,软件的repo地址
- [corpnewt](https://github.com/corpnewt)
  - https://github.com/corpnewt/GenSMBIOS
  - https://github.com/corpnewt/ProperTree
  - https://github.com/corpnewt/SSDTTime
