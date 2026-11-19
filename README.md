# MOAntiSpy

《心灵终结 3.3.6》（Mental Omega 3.3.6）的客户端插件。

> ## ⚠️ 使用范围
> **建议仅 PVE / 单人战役 / 人机对战使用。禁止在 PVP 中使用**——它会单方面废掉对方间谍。

## 功能

己方单位、建筑会自动优先攻击**攻击范围内**的敌方间谍。

- 全图扫描，不限于当前选中的单位；
- 只处理己方、有武器、且武器能对地的对象（纯对空武器如爱国者不参与）；
- 判定距离用该单位自己的武器射程；
- 每个单位每次扫描最多发一条指令，目标取范围内最近的间谍。

## 安装

1. 需要先安装 [Syringe](https://github.com/Ares-Developers/Syringe)（心灵终结自带）。
2. 把 `MOAntiSpy.dll`、`MOAntiSpy.dll.inj`、`MOAntiSpy.ini` 放进游戏根目录。
3. 界面选项：本包附带 `Resources\GameOptions.ini`，已加入「自动反间谍(单机)」复选框。
   - 原版未改动过：直接用包里的覆盖；
   - 已改过（装过其他插件）：手动把 `[chkAntiSpy]` 段追加到末尾，并把 `chkAntiSpy` 加到 `[MultiplayerGameLobby]` 和 `[SkirmishLobby]` 的 `CheckBoxes=` 行。

## 开关

- 游戏内「游戏规则」界面的 **自动反间谍(单机)** 复选框，勾选后生效，**默认不勾选**；
- 勾选状态由客户端写入 `spawn.ini` 的 `AntiSpy` 键，插件以它为准；
- 没有该界面时，可把 `MOAntiSpy.ini` 里的 `Enable` 改成 `1` 强制开启。

## 配置

```ini
[AntiSpy]
Enable=0         ; 0=关闭；spawn.ini 的勾选值优先
Interval=15      ; 扫描间隔（逻辑帧）
SpyTypes=        ; 额外间谍类型 ID；留空用内置 SPY/SPY2/SPY3/SPYF/SPYG/SPYS/SABOT
SkipAA=1         ; 纯对空武器不参与
Log=1
```

## 说明

- 纯客户端插件：只读对象状态并发送标准 Attack 事件，不修改模拟数据。
- 联机时对方无需安装（但请遵守 PVP 限制）。
- 被重定向的单位会离开当前任务去攻击间谍，扫描间隔可调大以减少打断。

## 兼容

- 心灵终结 3.3.6（gamemd + Syringe 0.7.3 + Ares 3.0p1）
