# 原神采集路线 CD 监控

一个纯本地、单文件 HTML 工具，拖拽 JSON 文件即可查看采集路线冷却剩余时间。

在线地址: https://this-fish.github.io/Read_BetterGI_JS_Pathing_CD/index.html

---

## ✨ 功能

- 拖拽 JSON 文件上传，自动解析
- 按物品自动分组，折叠 / 展开查看
- 显示剩余倒计时、预计刷新时间、进度条
- 支持多账户文件夹（自动识别子目录中的 `record.json`）
- 快捷键 `F1` / `0` 打开说明面板
- 深色 / 浅色模式自动切换（凌晨 0:00～6:30 深色）
- 数据完全在本地处理，不上传任何服务器

---

## 🚀 使用方法

1. **拖拽** `record.json` 到页面即可
2. 或按 `F3` 选择包含 `record.json` 的文件夹（多账户模式）
3. 或按 `F2` 选择单个 `record.json`（单账户模式）

---

## 📂 支持的 JSON 格式

| 来源工具 | 文件路径 |
|---------|---------|
| **采集cd管理**（4.0.0 前） | `JsScript\采集cd管理-me\record\[账号名]\record.json` |
| **AutoHoeingOneDragon** 锄地一条龙 | `JsScript\AutoHoeingOneDragon\records\[账号名].json` |
| **AbundantOre** 矿产资源批发 | `JsScript\AbundantOre-me\local\persistent_data.json` |
| **AutoFishingTeyvat** 提瓦特自动钓鱼 | `JsScript\AutoFishingTeyvat-\assets\archive.json` |
---

## ⌨️ 快捷键说明

| 按键 | 功能 |
|------|------|
| `F1` | 开启说明链接（GitHub） |
| `0` | 显示 / 隐藏快捷键面板 |
| `~` | 切换深色 / 浅色模式 |
| `Alt + F` | 切换全屏 |
| `[` | 启用 / 关闭自由编辑（调试用） |
| `F2` | 选择单个 `record.json` |
| `F3` | 选择包含 `record.json` 的文件夹 |


---

## ⏱️ CD 刷新周期

- 内置 `ITEM_CYCLE_MAP` 映射表，涵盖常见材料
- 未收录的物品默认 **24 小时**
- 进度条 = 剩余时间 ÷ 该物品周期，越接近刷新越满

---

## 🚫 不想显示某条路线

请依照**原文件的时间格式**，把该路线的时间值改成对应的「跳过值」：

### 若原文件是 ISO 字符串格式（UTC，结尾为 Z）
例如 `archive.json` 里是：

```json
"cdTime": "2026-09-28T20:00:00.000Z"
```

改成：

```json
"cdTime": "9970-01-01T00:00:00.000Z"
```

### 若原文件是 ISO 字符串格式

```json
"cdTime": "2026-09-28T00:00:00.000+08:00"
```

改成：

```json
"cdTime": "9970-01-01T08:00:00.000+08:00"
```

### 若原文件是毫秒时间戳格式
例如 `persistent_data.json` 里是：

```json
"last_run_time": 1790524800000
```

改成：

```json
"last_run_time": 252455616000000
```


## ⚠️ 注意事项

- 仅显示 **cdTime 大于当前时间** 的路线
- 页面每 **60 秒** 自动刷新一次倒计时
- 所有数据仅保存在内存中，刷新页面后需重新拖入


## 📝 更新日志

### 2026-09-17
- 修正 `persistent_data.json` 未匹配物品的路線進度條基準，改以 **72 小時** 計算
- 未匹配物品的分組名稱由「不明采集物」改為「**未標明**」
- 其他格式（`record.json`、`archive.json`）未匹配物品維持預設 **24 小時**

*更早版本包含显示路线进度功能及其他功能*