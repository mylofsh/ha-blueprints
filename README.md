# HA Blueprints

Home Assistant 自动化蓝图合集。

## 蓝图列表

### 房间窗户检查与窗帘纱帘联动

定时检查房间窗户是否关闭，未关则提醒并显示已开启时长；全关后自动闭合窗帘/纱帘。

**功能：**
- 支持定时两次检查（默认 18:00 和 20:00）
- 支持单选或多选窗户门磁
- 任意窗户未关即发送通知，并显示已开时长（如「客厅窗户（已开 2小时15分钟）」）
- 第 2 次检查时若所有窗户均已关闭，延时指定秒数自动合上窗帘/纱帘
- 第 1 次检查时若窗户全关则保持静默

**文件：** [`blueprints/automation/mylofsh/room_window_cover_sync.yaml`](blueprints/automation/mylofsh/room_window_cover_sync.yaml)

**导入方式：**

```
https://raw.githubusercontent.com/mylofsh/ha-blueprints/main/blueprints/automation/mylofsh/room_window_cover_sync.yaml
```

在 Home Assistant 中：**设置 → 自动化与场景 → 蓝图 → 导入蓝图**，粘贴上面的链接。

**配置项：**

| 配置项 | 说明 | 默认值 |
|---|---|---|
| 窗户门磁实体 | 该房间的窗户传感器，可多选 | — |
| 窗帘与纱帘实体 | 需要拉上的窗帘实体，可多选 | — |
| 第一次检查时间 | 仅检查并提醒，不关帘 | 18:00:00 |
| 第二次检查时间 | 检查窗户，全关后延时关帘 | 20:00:00 |
| 确认关窗后延时 | 确认窗户全关后等待多少秒再关帘 | 30 秒 |
| 推送通知服务 | 接收提醒的通知动作 | — |

**注意事项：**

- 通知服务需要选择具体的 `notify.*` 动作（如 `notify.mobile_app_iphone`）
- 蓝图使用 `expand()` 展开实体，支持设备选择和多实体选择
- 容器实体（如 `cover.curtain_group`）也可使用

## 许可

MIT
