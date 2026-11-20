# MOAntiSpy

《心灵终结 3.3.6》（Mental Omega 3.3.6）的客户端插件。

> ## 使用范围
> **仅建议 PVE / 单人战役 / 人机对战使用。**
> 联机安全性未验证，请勿在 PVP 中使用。

## 功能

己方**建筑**会自动攻击射程内的敌方间谍。

- 只处理己方建筑（防御塔这类有武器的建筑）；
- 只打"敌方"间谍，自己阵营的不会误伤；
- 目标距离超过 12 格不会开火（硬限制，避免跨图）；
- 建筑正在攻击其他目标时不会被打断。

## 安装

1. 需要先安装 [Syringe](https://github.com/Ares-Developers/Syringe)（心灵终结自带）。
2. 把 `MOAntiSpy.dll`、`MOAntiSpy.dll.inj`、`MOAntiSpy.ini` 放进游戏根目录。
3. 界面选项：本包附带 `Resources\GameOptions.ini`，已加入「自动反间谍(单机)」复选框。
   - 原版未改动过：直接用包里的覆盖；
   - 已改过（装过其他插件）：手动把 `[chkAntiSpy]` 段追加到末尾，并把 `chkAntiSpy` 加到 `[MultiplayerGameLobby]` 和 `[SkirmishLobby]` 的 `CheckBoxes=` 行。

## 开关

- 游戏内「游戏规则」界面的 **自动反间谍(单机)** 复选框，勾选后生效，**默认不勾选**；
- 勾选状态由客户端写入 `Client\SkirmishSettings.ini`，插件以它为准。

## 配置

```ini
[AntiSpy]
Enable=0         ; 0=关闭；界面勾选值优先
Interval=15      ; 扫描间隔（逻辑帧）
SpyTypes=SPY,SBTR,ARSO,INTRUDER,HIJACKER,REPU,CLAIR
SkipAA=1         ; 纯对空武器不参与
Log=0            ; 排查问题时改成 1
```

## 已知限制

- **只对建筑生效**，单位不参与（单位多武器槽会导致射程读错、单位乱跑，已移除）；
- 射程上限按 12 格硬限制，超过不会开火；
- 识别靠类型 ID，不依赖伪装。

## 兼容

- 心灵终结 3.3.6（gamemd + Syringe 0.7.3 + Ares 3.0p1）
