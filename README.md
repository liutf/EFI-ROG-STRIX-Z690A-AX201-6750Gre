# ASUS ROG STRIX Z690-A 黑苹果EFI配置

适用于华硕ROG STRIX Z690-A主板的OpenCore EFI配置，支持macOS 15 Sequoia系统。

<img width="3304" height="1610" alt="系统信息" src="https://github.com/user-attachments/assets/6e6ae815-27e6-4bd5-b8de-2a45028e4459" />

## OpenCore版本

[OpenCore 1.0.6](https://github.com/acidanthera/OpenCorePkg)

## 支持的操作系统版本

- macOS Sequoia 15.x

## 硬件配置清单

| 组件 | 型号 |
|------|------|
| CPU | 英特尔 i9-13900K ES(Q0PU) |
| 主板 | ROG STRIX Z690-A GAMING WIFI D4 |
| 显卡 | 蓝宝石 RX6750GRE 12G 黑钻 |
| 内存 | 海盗船复仇者 DDR4 3200MHz 16G × 2 |
| SSD1 | 铠侠 RC20 1T (MacOS15.5) |
| SSD2 | 希捷芯点子 C700 2T (Win11) |
| SSD3 | 致钛 TiPlus 7100 1T (NTFS) |
| HDD | TOSHIBA 3T (NTFS) |
| 无线网卡 | 英特尔 Wi-Fi AX201 |
| 电源 | 鑫谷 AN750 750W |
| 散热 | 利民 PA120 SE 塔式 |
| 机箱 | 玩嘉 玄武 PLUS 海景房 |

## BIOS设置

| 选项 | 设置 |
|------|------|
| VT-d | Enabled |
| Above 4G Decoding | Enabled |
| CSM | Disabled |
| Resize Bar Support | Enabled |
| XHCI-Hand-Off | Enabled |
| Fast Boot | Disabled |
| Secure Boot | Disabled |

[黑苹果之华硕ASUS主板BIOS详细设置篇](https://www.bilibili.com/opus/439170520668179105?spm_id_from=333.999.0.0)

## 使用说明

1. **SMBIOS配置**
   - 使用 [OpenCore Configurator](https://mackie100projects.altervista.org/opencore-configurator/) 构建您的SMBIOS信息

2. **CFG Lock解锁**
   - 在安装黑苹果之前，必须使用 [RU.efi](RU.efi) 解锁 `CFG LOCK`
   - 可以观看我的 [教学视频](https://www.bilibili.com/video/BV1LV4y1N7jF) 了解详细操作步骤

## EFI目录结构

```
EFI/
├── BOOT/
│   └── BOOTx64.efi
├── OC/
│   ├── ACPI/           # ACPI补丁
│   ├── Drivers/        # 驱动程序
│   ├── Kexts/          # 内核扩展
│   ├── Resources/      # 资源文件
│   ├── Tools/          # 工具
│   ├── config.plist    # 主配置文件
│   └── OpenCore.efi    # OpenCore引导程序
```

## 核心驱动组件

- **Lilu.kext**: 系统扩展框架
- **VirtualSMC.kext**: SMC模拟器
- **AppleALC.kext**: 音频驱动
- **IntelBluetoothFirmware.kext**: 英特尔蓝牙驱动
- **LucyRTL8125Ethernet.kext**: 网络驱动
- **CPUFriend.kext**: CPU电源管理
- **USBToolBox.kext**: USB定制工具

## ACPI补丁说明

- **SSDT-AWAC.aml**: 修复AWAC时钟
- **SSDT-EC-USBX.aml**: USB电源属性修复
- **SSDT-GPRW.aml**: USB唤醒修复
- **SSDT-PLUG-ALT.aml**: CPU电源管理修复

## 系统截图
- Geekbench 6 + Cinebench R23 性能测试


## 常见问题

**Q: 为什么需要解锁CFG Lock？**
A: CFG Lock限制了CPU的一些高级电源管理功能，解锁后可以获得更好的性能和稳定性。

**Q: 为什么蓝牙不能正常使用？**
A: 确保已正确安装IntelBluetoothFirmware.kext和IntelBTPatcher.kext驱动。

**Q: USB端口如何定制？**
A: 使用USBToolBox.kext和USBPort.kext进行定制，避免USB端口数量限制。

## 更新日志

- v1.0.6: 升级至OpenCore 1.0.6版本
- v1.0.0: 初始版本发布

## 联系方式

QQ群: 23304408
如有问题或建议，可在QQ群中反馈。