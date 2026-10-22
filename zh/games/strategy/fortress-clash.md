# 堡垒冲突

<a href="https://inkwengame.com/zh/games/fortress-clash" target="_blank" rel="noopener noreferrer">在 InkwenGame 玩</a>

![cover](https://img.inkwengame.com/games/fortress-clash/cover.jpg)

已修复已报告的问题：重新加载后进度无法恢复。

## 怎么玩

从底部托盘中选择一个方块或单位，然后点击网格将其放置在你的推车上，建造你的堡垒和军队。方块需要消耗金币；每次胜利都会获得金币奖励，并允许你选择额外奖励。点击“战斗”按钮即可开始——你的弓箭手和单位会自动攻击敌方堡垒。击败敌方国王即可获胜：将他从推车上击落、用瓦砾掩埋或炸毁他的城墙。在升级界面花费金币可以提升单位等级并解锁新武器（大炮、弩、激光、手榴弹）。使用鼠标或触摸操作即可畅玩——无需键盘。

## 介绍

已修复已报告的问题：重新加载后进度无法恢复。

根本原因：`bridge.storage.get()` 返回的已保存值已被解析为对象，而游戏预期的是 JSON 字符串，因此再次解析，导致抛出异常并静默丢弃了存档。

更改：

- `storage.get()` 现在接受对象和字符串两种格式。

- 存档在游戏画面显示之前加载：会显示加载界面，并且在 `storage.get()` 解析完成之前，所有输入都会被忽略，因此新的默认存档不会在启动时覆盖实际进度。

- 存档带有版本计数器，因此在“完成关卡并购买升级”后，最新版本始终优先于同一关卡的旧版本。

- 页面隐藏/卸载时，所有待处理的写入都会被清除，因此重新加载前的最后操作不会丢失。

已在 QA 工具中验证：重新加载游戏前写入的状态在重新加载后会完全恢复。

## 详情

- 分类: <a href="https://inkwengame.com/zh/strategy" target="_blank" rel="noopener noreferrer">策略</a>
- 画面方向: portrait
- 可玩设备: desktop, mobile
- 游戏语言: en
- 开发者: Playgama
- 标签: 策略, 塔防
