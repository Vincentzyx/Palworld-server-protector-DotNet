# Palworld-server-protector-DotNet
【新】GUI版本 Palworld服务端进程守护+内存监控+优雅重启+自动存档+Rcon
（for windows）


注意：protector-electron（旧版）已弃用

## 功能
- 内存监控（自定义阈值触发）
- 进程守护（当前如果没有服务端运行就自动重启）
- 优雅重启（内存占用达到阈值后自动发送公告并关服等待重启）
- 自动备份存档
- 轮询获取在线玩家
- Rcon指令
- 新功能待添加

## 注意
- 本GUI版本复刻了命令行版本（[https://github.com/KirosHan/Palworld-server-protector](https://github.com/KirosHan/Palworld-server-protector)）所有功能
- 旧GUI版（electron）由于占用内存过高已弃用并不再维护

## 效果图
![预览](https://raw.githubusercontent.com/KirosHan/Palworld-server-protector-DotNet/main/PNG/screen.png)

## 直接下载（懒人专属）

[Releases](https://github.com/KirosHan/Palworld-server-protector-DotNet/releases)

如无法运行，请安装.net 6.0运行环境

## Star and a Coffee

如果这个仓库对你有用，欢迎点个Star⭐︎

也可以Buy me a coffee☕︎

![BuyMeACoffee](https://raw.githubusercontent.com/KirosHan/Palworld-server-protector-DotNet/main/PNG/buymeacoffee.png)

## 编译运行
Visual studio 2022


## 运行逻辑

```mermaid
graph TD
    A[开始] --> B[检查内存使用]
    B --> C{检查是否超过预设阈值}
    C -- 是 --> D[发送重启命令并重启]
    C -- 否 --> E[检查进程是否运行]
    E -- 是 --> F[等待下一个监控周期]
    E -- 否 --> G[启动进程]
    G --> F
    D --> F
    A --> H[定时备份游戏存档]
    H --> I[等待下一个备份周期]
    I --> H
```
## 已知问题
1.受服务端限制，rcon发送的文本中无法保留空格，已自动替换为下划线

2.受服务端限制，rcon无法发送中文

