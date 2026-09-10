# bugensui2022 的公开资源物料库

这里是 bugensui2022 的各类 Home Assistant 前端卡片、插件及实用公开物料。所有文件均经过实测与长期稳定运行，欢迎大家按需下载使用。

---

## 📦 物料列表清单
 **`cyber-energy-dashboard.js`** | HA卡片 | 赛博朋克风家庭电表监控大屏卡片，支持实时功率旋转表盘与环比统计。 
 
 **`cyber-guest-wifi.js`** | HA卡片 | 赛博朋克风访客Wi-Fi全景大屏卡片，支持扫码免密直连、密码一键复制、3D全息机甲舱与路由器遥测 

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


cyber-guest-wifi.js HA卡片配置方式

```yaml
type: custom:cyber-guest-wifi
# ==========================================
# 1. 顶部标题与副标题个性化配置
# ==========================================
title_main: "访客"                      # 顶部大标题（白色主字）
title_highlight: "网络"                 # 顶部大标题高亮词（赛博金色发光字）
title_subtitle: "SECURE GUEST ACCESS NODE // 5.0GHz / 2.4GHz"  # 标题下方科技副标
clock_subtitle: "STATUS: BROADCASTING // OPERATIONAL"          # 时钟下方广播状态文字

# ==========================================
# 2. Wi-Fi 连接凭证与协议配置
# ==========================================
wifi_ssid: "Cyber_Guest_5G"            # 访客 Wi-Fi 名称 (SSID)
wifi_password: "guest_password_666"    # 访客 Wi-Fi 密码（支持在卡片上一键点击复制）
encryption_type: "WPA"                 # 加密方式：WPA、WPA2、WPA3、WEP 或 nopass（无密码）
wifi_standard: "Wi-Fi 7 BE6500"        # 路由器机甲舱顶部显示的规格标牌
band_spec: "5.0 GHz / 2.4 GHz DUAL-BAND" # 频段规格标识

# ==========================================
# 3. 路由器展示舱与动画特效配置
# ==========================================
# 路由器正面/透明免抠图路径，请将图片放置在 HA 的 /config/www/ 目录下
router_image: "/local/default_router.png"  

# 路由器动画开关：
# true  = 开启围绕中心点平滑旋转的全息雷达扫描动效（赛博科技感）
# false = 关闭动画，路由器保持静止居中原样
router_animation: true                  

# ==========================================
# 4. 可选：自定义二维码图片
# ==========================================
# 默认情况下卡片会根据上面的 ssid 和 password 自动生成国际标准 Wi-Fi 免密直连二维码；
# 如果您想使用自己微信/特定格式的二维码图片，可以取消下方注释并填入图片路径：
# qr_image: "/local/my_custom_qr.png"

# ==========================================
# 5. Home Assistant 传感器遥测实体绑定
# ==========================================
entities:
  client_count: sensor.router_online_clients    # 当前在线设备数传感器实体（填您的实际实体ID）
  cpu_temp: sensor.router_cpu_temperature       # 路由器 CPU 温度传感器实体（填您的实际实体ID）
```

## 📥 下载方式
进入仓库右侧的 [Releases 发布区](https://github.com/bugensui2022/ziyuan/releases) 即可高速下载最新版单文件。
