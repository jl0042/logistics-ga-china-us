# 数据档案 (data/)

本目录存放 `index.html` 中所有图表使用的原始数据 + 方法论文档。每个 CSV 对应若干图表, 字段都有 `source_url` 列, 方便逐项核对。

---

## 文件清单

### Section 1 — 地理与经济

| 文件 | 内容 | 行数 |
|---|---|---|
| `s1_cn_provinces.csv` | 中国 31 省 (含港澳台): 人口密度 / 人均 GDP / 民用机场 / 面积 / 2024 人口, 各省统计局 2024 公报 | 33 |
| `s1_us_states.csv` | 美国 50 州 + DC: 人均 GDP / 人口 / FAA NPIAS 机场细分 (Primary/Nonprimary/Reliever/GA) | 51 |
| `s1_cn_cities.csv` | 中国 Top 35 城市 GDP + 经纬度 (累计覆盖全国 GDP ~60%), 各市统计局 2024 公报 | 35 |
| `s1_us_metros.csv` | 美国 Top 35 MSA GDP + 经纬度 (累计覆盖 ~65%), BEA Real GDP by Metropolitan Area 2023 | 35 |
| `s1_cargo_hubs.csv` | 中国 10 大 + 美国 10 大货运机场: 坐标 + cargo 量 + 排名, ACI 2024 + 公司年报 | 22 |
| `s1_airport_counts.csv` | 机场口径方法论: CAAC vs FAA NPIAS vs FAA 全部 (含私用) 三个口径数字 + 解释 | — |

### Section 2 — 基础设施差距

| 文件 | 内容 | 行数 |
|---|---|---|
| `s2_freight_modes.csv` | 中美 2024 货运分模式 (公路/铁路/水运/民航/管道) 中国 MOT 公报直接给出, 美国 ATA+AAR+USACE 综合 | 14 |
| `s2_air_cargo.csv` | 民航货运三种口径 (国内运输量 / 总运输量 / 机场吞吐量) 中美对比 + Top 10 机场 + 估算来源 | 15 |
| `s2_express_parcels.csv` | 中美 2024 快递包裹: 中国国家邮政局 1750.8 亿件 (含同城/异地/国际拆分); 美国 ShipMatrix 238 亿件 (按 USPS/Amazon/UPS/FedEx 拆分) | 9 |
| `s2_logistics_cost.csv` | 中美 2024 物流成本: CFLP 19.0 万亿 / 14.1% vs CSCMP $2.58T / 8.8% + 子项拆分 (运输/库存/管理) | 14 |
| `s2_aircraft_fleet.csv` | 中美飞机 + 机场数: CAAC 4394 运输机 / 3232 通航 + FAA NPIAS 3287 + GA Survey 204K | 14 |
| `s2_highway_distribution.csv` | 中国高速公路 19.07 万 km 东/中/西部分布 + 4 大省细节 | 8 |
| `s2_comparison_analysis.md` | S2 完整对比分析 + 6 项交叉验证 + 修正前后对比 + 数据局限 | (markdown) |

### 辅助文件

| 文件 | 内容 |
|---|---|
| `ARP-NPIAS-2025-2029-AppendixA.xlsx` | FAA NPIAS 2025-2029 原始 Excel (从 FAA 官网下载, 用于 S1/S2 美国机场数据) |

---

## 数据约定

### 编码
- 所有 CSV 用 **UTF-8 BOM** 编码 (`utf-8-sig` in Python), 保证 Excel 打开不乱码

### 通用字段 (S2 引入的标准模式)
按 `source_url` 列标注每行数据的官方来源 URL。多数 CSV 含以下字段:

| 字段 | 含义 | 示例 |
|---|---|---|
| `value` 或具体名 | 数据值 | `418.80` |
| `unit` | 单位 (中文) | `亿吨`, `万吨`, `亿元`, `亿件` |
| `year` | 数据年份 | `2024` |
| `source_org` | 数据原始机构 | `交通运输部`, `CAAC`, `BEA`, `ATA` |
| `source_doc` | 具体公报/报告名 | `2024 年交通运输行业发展统计公报` |
| `source_url` | 直接 URL | `https://...` |
| `status` | 数据可信度 | `verified` / `partial` / `unverified` / `needs_update` |
| `notes` | 备注 (口径、同比、估算逻辑等) | `同比 +3.8%; 营业性公路货运量` |

### `status` 含义
- `verified` ✅ — 直接从官方原始文档 (公报、年报、统计页) 抓取或核对过
- `partial` ⚠️ — 部分核对, 主要数字 verified 但子项是基于占比反推
- `unverified` 🟡 — 估算或综合多源, 有 ±10-30% 误差
- `needs_update` 🟠 — 已知数据陈旧, 待找新源

### 单位约定
- **中国**: 亿吨, 万吨, 亿元 (人民币), 亿件, 万亿
- **美国**: short tons (短吨, 1 short ton = 0.907 公吨), $billion, $trillion
- **国际可比**: 公制吨 (metric tons / tonnes), 美元
- 跨国对比时需要转换: short ton × 0.907 → 公吨; $ × 汇率 (2024 年均 7.20) → 元

---

## 数据源优先级

按 [MEMORY.md](../../../.claude/projects/.../memory/MEMORY.md) 的 `data_source_convention` 规范:

1. **官方网站** (政府/监管机构: NBS / MOT / CAAC / 国家邮政局 / FAA / BTS / BEA / Census)
2. **行业协会** (有方法论披露: ATA / AAR / USACE / CSCMP / IATA / ACI)
3. **Wikipedia** (引用原始源, 适合作为索引)
4. **行业研报/媒体** (FreightWaves, Supply Chain Dive, Logistics Mgmt — 注明)
5. **公司年报** (USPS/UPS/FedEx/Amazon 10-K — 注明财年)

**禁用** ❌: 微信公众号、百家号、知乎、抖音、CSDN 博客、个人博客 (除非引用原始源)

---

## 交叉验证方法

跨国对比时, 即使两国统计口径不同 (中国营业性发送量 vs 美国 BTS Freight Facts), 至少要做以下几种验证:

1. **占比结构相似度**: 公路/铁路/水运/航空/管道占比是否合理 (例: 中美公路+铁路占比都 ~83%)
2. **人均量验证**: 两国人均货运、人均快递是否在同数量级 (例: 人均货运中美都 ~40 公吨/人)
3. **不同口径自洽**: 同一国不同口径数字之间比例是否合理 (例: 中国机场吞吐量 / 航空公司运输量 = 2.23 ≈ 平均每票货过 2 个机场)
4. **时间序列**: 同一指标历年趋势是否合理 (例: 美国 2020 BTS 25.1B lbs → 2021 boom → 2023 -10% → 2024 略复苏)
5. **绝对值汇率换算**: 货币类指标按汇率换算后是否相当 (例: CSCMP $2.58T × 7.20 = 18.6 万亿元 ≈ CFLP 19.0 万亿)
6. **国际机构交叉**: ICAO / IATA / OECD / World Bank 同主题数据是否对得上

具体执行见 [`s2_comparison_analysis.md`](./s2_comparison_analysis.md) 的 6 项验证示例。

---

## 工作流 (每个 section)

每节 review 时按这个流程:

1. **用户提出 challenge** (例: "为什么中国民航 2006 万吨?")
2. **Claude 找官方源** (按数据源优先级)
3. **Claude 做交叉验证** (口径相似度 / 人均 / 时间序列等)
4. **Claude 写入 / 更新 CSV** (含 `source_url` + `status`)
5. **Claude 同步更新 `index.html`** (chart 数据 + chart-desc + source 行 + insight 文本)
6. **Claude 检查其他 section 是否引用旧数据** (grep 关键词)
7. **Claude commit + push**

---

## 已知数据局限

记录在 CSV 中 `status=unverified` 或 `partial` 的项目, 主要是:

### 美国分模式精确公制吨
- BTS Freight Facts and Figures 公开页面访问受限 (.gov 域 fetch 403)
- 当前美国货运分模式数字基于 ATA 11.27B short tons + AAR 占比 10.6% + USACE/EIA 估算反推
- 误差 ±10%

### 美国国内 air cargo 2024
- BTS T-100 segment data 公开摘要不可访问
- 估算基于 BTS 2020 baseline (25.1B lbs = 1140 万吨) + Statista FedEx/UPS 2021 ton-miles + 2023 -10% + 2024 略复苏
- 估算 ~1,250 万吨 (range 1,100-1,400)
- 误差 ±20%

### 美国管道运输量
- EIA 提供 capacity (Bcf/day) 不直接给 tons/year
- 当前 ~30 亿公吨是 FAF 5.7 历史推算

### 中国管道运输量
- MOT 营业性公报不含管道
- 国家能源局给主干网络 10 万 km 但不给年运输量
- 网页处理: 中国直接不显示管道项

---

## 编辑者注意

如果 `index.html` 里改了数字, **必须同步**:
1. 该数字对应的 CSV 行 (`value` + `notes` 注明改动原因)
2. 该图表的 `<div class="source">` 行 (按规范)
3. 检查其他 section 是否也引用 (grep 旧值)

不要在 CSV 里写"我改成什么了"这种内部沟通, 只写客观数据 + 来源 + 现状。

写作风格规范见: [`MEMORY.md`](../../../.claude/projects/.../memory/MEMORY.md)
