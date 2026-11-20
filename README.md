# MOAntiSpy

《心灵终结 3.3.6》（Mental Omega 3.3.6）的客户端插件。

> ## 使用范围
> **仅建议 PVE / 单人战役 / 人机对战使用。** 联机安全性未验证。

## 功能

己方**建筑**会自动攻击射程内的敌方间谍。

- 只处理己方建筑（防御塔这类有武器的建筑）；
- 只打敌方间谍，自己阵营的不会误伤；
- 目标超过 12 格不开火（硬限制）；
- 建筑正在打别的目标时不会被打断。

## 安装

1. 需要 Syringe（心灵终结自带）。
2. 把 `MOAntiSpy.dll`、`MOAntiSpy.dll.inj`、`MOAntiSpy.ini` 放进**游戏根目录**（gamemd.exe 所在目录）。

## 开启方法（二选一）

### 方法一：界面选项（推荐）

在游戏的「游戏规则」界面里勾选 **自动反间谍(单机)**。

如果你的界面里**没有**这个选项，需要手动往 `Resources\GameOptions.ini` 里加两处：

1）在文件末尾追加：

```ini
[chkAntiSpy]
OptionName=AntiSpy
Text=自动反间谍(单机)
SpawnIniOption=AntiSpy
Checked=False
Location=1133,134
ToolTip=仅单机:己方建筑优先攻击射程内的敌方间谍
```

2）找到 `[MultiplayerGameLobby]` 和 `[SkirmishLobby]` 两个节里的 `CheckBoxes=` 行，在末尾加上 `,chkAntiSpy`。

改之前请先备份 `GameOptions.ini`。

### 方法二：直接改 ini

不想动 GameOptions.ini 的话，把 `MOAntiSpy.ini` 里的 `Enable=0` 改成 `Enable=1` 即可强制开启。

## 配置

```ini
[AntiSpy]
Enable=0
Interval=15
SpyTypes=SPY,SBTR,ARSO,INTRUDER,HIJACKER,REPU,CLAIR
SkipAA=1
Log=0
```

## 已知限制

- **只对建筑生效**，单位不参与；
- 射程上限 12 格；
- 识别靠类型 ID，不看伪装。

## 兼容

- 心灵终结 3.3.6（gamemd + Syringe 0.7.3 + Ares 3.0p1）
