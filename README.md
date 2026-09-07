# bugensui2022 的公开资源物料库

这里是 bugensui2022 分享的各类 Home Assistant 前端卡片、插件及实用公开物料。所有文件均经过实测与长期稳定运行，欢迎大家按需下载使用。

---

## 📦 物料列表清单
| **`cyber-energy-dashboard.js`** | HA卡片 | 赛博朋克风家庭电表监控大屏卡片，支持实时功率旋转表盘与环比统计。 |

cyber-energy-dashboard.js HA卡片配置方式

```yaml
type: custom:cyber-energy-dashboard
title_main: 家庭
title_highlight: 电表
title_subtitle: HOME ENERGY MONITORING MATRIX
clock_subtitle: Real-time Streaming
entities:
  # --- 1. 实时电气数据 ---
  realtimePower: sensor.esp_power             # 实时功率 (单位: W 或 kW)
  powerFactor: sensor.esp_power_factor         # 功率因数 (数值: 0.00 - 1.00)
  realtimeVoltage: sensor.esp_voltage         # 实时电压 (单位: V)
  realtimeCurrent: sensor.esp_current         # 实时电流 (单位: A)

  # --- 2. 当前阶梯与实时电价 ---
  currentTier: sensor.esp_meter_dqjtqk        # 当前阶梯情况 (如: 第一阶梯、二档等)
  currentPrice: sensor.esp_meter_current_price # 当前电价单价 (单位: 元/kWh)

  # --- 3. 今日与昨日用电/电费 ---
  todayEnergy: sensor.esp_meter_today_usage           # 今日用电量 (单位: kWh)
  yesterdayEnergy: sensor.esp_meter_yesterday_usage   # 昨日用电量 (卡片底部对比项)
  todayCost: sensor.esp_meter_today_bill              # 今日电费 (单位: 元)
  yesterdayCost: sensor.esp_meter_yesterday_bill      # 昨日电费 (卡片底部对比项)

  # --- 4. 本月与上月用电/电费 ---
  thisMonthEnergy: sensor.esp_meter_month_usage       # 本月用电量 (单位: kWh)
  lastMonthEnergy: sensor.esp_meter_last_month_usage  # 上月用电量 (卡片底部对比项)
  thisMonthCost: sensor.esp_meter_month_bill          # 本月电费 (单位: 元)
  lastMonthCost: sensor.esp_meter_last_month_bill      # 上月电费 (卡片底部对比项)

  # --- 5. 年度用电与电费 (可选) ---
  thisYearEnergy: sensor.esp_meter_annual_usage       # 本年累计用电 (单位: kWh)
  lastYearEnergy: sensor.esp_meter_last_annual_usage  # 去年同期用电
  thisYearCost: sensor.esp_meter_annual_bill          # 本年累计电费 (单位: 元)
  lastYearCost: sensor.esp_meter_last_annual_bill      # 去年同期电费
```
---

## 📥 下载方式
进入仓库右侧的 [Releases 发布区](https://github.com/bugensui2022/ziyuan/releases) 即可高速下载最新版单文件。
