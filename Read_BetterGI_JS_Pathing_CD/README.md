# 原神采集路线 CD 监控

一个纯本地、单文件 HTML 工具，拖拽 JSON 文件即可查看采集路线冷却剩余时间。

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

| 来源工具 | 檔案路徑 |
|---------|---------|
| **采集cd管理**（4.0.0 前） | `JsScript\采集cd管理-me\record\[帳號名]\record.json` |
| **AutoHoeingOneDragon** 锄地一条龙 | `JsScript\AutoHoeingOneDragon\records\[帳號名].json` |
| **AbundantOre** 矿产资源批发 | `JsScript\AbundantOre-me\local\persistent_data.json` |
| **AutoFishingTeyvat** 提瓦特自动钓鱼 | `JsScript\AutoFishingTeyvat-\assets\archive.json` |
---

## ⌨️ 快捷键

| 按键 | 功能 |
|------|------|
| `F1` | 開啟說明連結（GitHub） |
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

## 🚫 不想顯示某條路線

請依照**原檔案的時間格式**，把該路線的時間值改成對應的「跳過值」：

### 若原檔案是 ISO 字串格式（UTC，結尾為 Z）
例如 `archive.json` 裡是：

```json
"cdTime": "2026-09-28T20:00:00.000Z"
```

改成：

```json
"cdTime": "9970-01-01T00:00:00.000Z"
```

### 若原檔案是 ISO 字串格式

```json
"cdTime": "2026-09-28T00:00:00.000+08:00"
```

改成：

```json
"cdTime": "9970-01-01T08:00:00.000+08:00"
```

### 若原檔案是毫秒時間戳格式
例如 `persistent_data.json` 裡是：

```json
"last_run_time": 1790524800000
```

改成：

```json
"last_run_time": 252455616000000
```


## ⚠️ 注意事項

- 僅顯示 **cdTime 大於當前時間** 的路線
- 頁面每 **60 秒** 自動刷新一次倒計時
- 所有數據僅保存在內存中，刷新頁面後需重新拖入

---

