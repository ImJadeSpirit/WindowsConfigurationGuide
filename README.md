# Windows 开荒指北

> # 摘要
> 本项目是旨在为部署个人用户的 Windows 提供一些指导，而本自述文件主要写对新安装的 Windows 进行部署可能需要用到的命令、链接。

## 一、命令

### （一）BitLocker

查看驱动器 BitLocker 状态的命令为
```
manage-bde -status
```

记 α 为要禁用 BitLocker 的驱动器盘符，禁用 BitLocker 的命令为
```
manage-bde -off α
```

### （二）MAS

```
irm https://get.activated.win | iex
```

### （三）保留的存储

查询保留存储状态命令为
```
dism /Online /Get-ReservedStorageState
```
禁用保留存储命令为
```
dism /Online /Set-ReservedStorageState /State:Disabled
```

### （四）右键菜单切换

切换为旧版右键菜单命令为
```
reg add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve
```
切换为新版的右键菜单命令为
```
reg delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /va /f
```

### （五）快速启动

检查快速启动开启状态命令为
```
(GP "HKLM:\SYSTEM\CurrentControlSet\Control\Session Manager\Power")."HiberbootEnabled"
```
返回值`1`表示快速启动已打开，`0`表示快速启动为关闭。

1. 打开组策略编辑器并打开“计算机配置\管理模板\系统\关机\要求使用快速启动”，选择禁用以关闭快速启动，单击应用和确定保存更改。
1. 若要关闭快速启动，创建一个 txt 文件，输入
```
Windows Registry Editor Version 5.00
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Power]
"HiberbootEnabled"=dword:00000000
```
并另存为文件名为 `Disable_fast-startup.reg` 、类型为所有文件的注册表项文件并运行；若要启用快速启动，创建一个 txt 文件，输入
```
Windows Registry Editor Version 5.00
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Power]
"HiberbootEnabled"=dword:00000001
```
并另存为文件名为 `Enable_fast_startup.reg` 、类型为所有文件的注册表项文件并运行。

## 二、安装

### （一）应用程序安装

通常地， PC 需要以下方面的应用：

+ **浏览器**，如 Microsoft Edge, Google Chrome, Mozilla Firefox
+ **视频播放器**，如 VLC media player
+ **音乐播放器**，如 Coriander
+ **PDF文档查看与处理**，如 PDF24
+ **图片查看器**，如 ImageGlass, FastStone Image Viewer
+ **文件查找**，如 Everything, Anytxt Searcher, Listaty
+ **文件格式转换**，如 File Converter
+ **邮件客户端**，如 Thunderbird
+ **局域网文件传输**，如 LocalSend
+ **压缩**，如 Bandizip，7zip, WinRAR
+ **办公套件**，如 Microsoft Office, WPS Office
+ **截图、贴图**，如 PixPin, Snipaste
+ **录屏**，如 PixPin, OBS Studio
+ **加速 Steam 等连接**，如 Steamcommunity_302, Watt Toolkit
+ **工具箱**，如 PowerToys
+ **卸载工具**，如 HiBit Uninstaller
+ **垃圾清理**，如 Dism++, HiBit Uninstaller
+ **系统优化**，如 ZyperWin++, Dism++

此外，值得一提的还有 GitHub 项目 [Adobe 旗下应用替代](https://github.com/KenneyNL/Adobe-Alternatives "Adobe Alternatives") 。

一般情况下，可以通过以下途径为 PC 安装应用：

#### (1)使用 UniGetUI 安装

> [UniGetUI][UniGetUI] 可通过 [主页][UniGetUI] 、[微软商店][UniGetUI-on-MSstore] 或 [GitHub][GETUniGetUI-on-GitHub] 下载 [安装程序][GETUniGetUI] 。

本项目中的 UniGetUI 捆绑包 `软件捆绑包.ubundle` 中包含有如下应用：
* 企业微信
* Ditto
* Everything
* File Converter
* Thunderbird
* PowerToys
* QQ
* Sandboxie-Plus
* Steam
* 腾讯会议
* 微信
* Zotero
* VLC media player
* OBS Studio
* ImageGlass
* AnyTXT Searcher
* PDF24
* qBittorrent
* Listary
* PixPin
* VS Code

#### (2)从官网安装

#### (3)从微软商店安装

> 安装之前记得去存储设置（`ms-settings：storagesense`）中的`保存新内容的地方`改微软商店应用安装位置

### （二）浏览器扩展安装

| 扩展名称 | 扩展商店 | 扩展主页 | 简介 |
| :----: | :----: | :----: | :---- |
| AdGuard 广告拦截器 | [Microsoft Edge 加载项](https://microsoftedge.microsoft.com/addons/detail/adguard-广告拦截器/pdffkfellgipmhklpdmokmckkkfcopbh) | [GitHub](https://github.com/AdguardTeam/AdguardBrowserExtension/releases/tag/v5.1.139) | 广告拦截扩展 |
| BewlyCat | [Microsoft Edge 加载项](https://microsoftedge.microsoft.com/addons/detail/bewlycat/aaammfjdfifgnfnbflolojihjfhdploj) | [GitHub](https://github.com/keleus/BewlyCat/) | 哔哩哔哩加强 |
| iTab新标签页 | [Microsoft Edge 加载项](https://microsoftedge.microsoft.com/addons/detail/itab新标签页/inedkoakiaeepjoblbiiipedngonadhn) | [官网](https://www.itab.link/) | 更佳的新标签页 |
| pakku：哔哩哔哩弹幕过滤器 | [Microsoft Edge 加载项](https://microsoftedge.microsoft.com/addons/detail/pakku：哔哩哔哩弹幕过滤器/lnfcfeidnipnphibahlkdhalpkpmccoc) | [GitHub](https://github.com/xmcp/pakku.js/) | 哔哩哔哩弹幕过滤 |
| 为Browser™启用右键 | [Microsoft Edge 加载项](https://microsoftedge.microsoft.com/addons/detail/为browser™启用右键/lbnohfpkjobaompkendjljgljpmldpoa) | [官网](https://enable-rightclick.freebusinessapps.net/) | 重新启用浏览器的右键 |
| 小电视空降助手 | [Microsoft Edge 加载项](https://microsoftedge.microsoft.com/addons/detail/小电视空降助手/khkeolgobhdoloioehjgfpobjnmagfha) | [GitHub](https://github.com/hanydd/BilibiliSponsorBlock) | 跳过哔哩哔哩视频片段 |
| 简悦 - SimpRead | [Microsoft Edge 加载项](https://microsoftedge.microsoft.com/addons/detail/简悦-simpread/clgdhlhfiocphghdkdbgdlmfaafccfmc) | [官网](https://simpread.pro/) | 进入沉浸的阅读模式 |
| 篡改猴 | [Microsoft Edge 加载项](https://microsoftedge.microsoft.com/addons/detail/篡改猴/iikmkjmpaadaobahmlepeloendndfphd) | [GitHub](https://github.com/Tampermonkey/tampermonkey) | 使用用户脚本自由地改变网页 |
| ENO-M | [Chrome Web Store](https://chromewebstore.google.com/detail/hjcdffalgapcchmopkbnkljenlglloln) | [GitHub](https://github.com/Cteros/eno-music) | 哔哩哔哩音乐 |
| Microsoft automatic rewards | [Chrome Web Store](https://chromewebstore.google.com/detail/ocmmbfdhomnkljmjkmafegefcgcfkefo) | [GitHub](https://github.com/spin311/MicrosoftRewardsWebsite) | 自动获取必应奖励 |


[profile]: https://github.com/ImJadeSpirit "GitHub 个人主页"
[UniGetUI]: https://www.marticliment.com/unigetui/ "UniGetUI 主页"
[UniGetUI-on-MSstore]: https://apps.microsoft.com/detail/xpfftq032ptphf "UniGetUI 微软商店页面"
[GETUniGetUI-on-GitHub]: https://github.com/marticliment/UniGetUI "UniGetUI GitHub页面"
[GETUniGetUI]: https://github.com/marticliment/UniGetUI/releases/latest/download/UniGetUI.Installer.exe "UniGetUI 安装程序"
