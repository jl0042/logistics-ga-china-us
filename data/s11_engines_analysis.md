# S11 发动机候选库 — 调研分析

## 数据范围

`s11_engines.csv` 共 23 行, 覆盖:
- AECC 国产: 12 行 (AES100 / AEP100 / AEP100-A / AEP60E / AEP50 / AEP500 / WJ-6 / WJ-6C / WJ-9 / 1100kW 涡轴 / AES20)
- 宗申活塞: 4 行 (C115 / C145 / CA500 / CA510)
- Rotax 进口: 4 行 (912 ULS / 914 UL / 915 iS / 916 iS)
- PWC 进口: 5 行 (PT6A-114A / PT6A-67B / PT6A-65 / PW127M / PW127XT / PW150A — 合并为 5 主条)

## 2026-04-26 增补
- WJ-6 行: 补 "2025-04 AECC 南方首批 2 台交付 8-10t 级 UAV 项目"——军用涡桨民用化第一步
- 新增 WJ-6C 行 (2,350 kW / 3,150 SHP / SFC 0.74 / 干重 ~1,000 kg, 军用预警机平台用)
- 用户问 "AEP400 + WJ-6C 是否在 CM100" 的问题: AEP400 在 AECC 官方产品目录中**不存在**, 仅自媒体推测; CM100 官方未公布发动机型号, 仅展出 1:10 模型
- CM100 研制方: 沈阳重明航空科技 (主导, 辽宁地方平台持股 94.12%) + 沈飞 / 626 所合计 3.53% (小股东)——常被误传为"沈飞推出"

---

## 1. 5 款主力 UAV 实际配套现状

| UAV | MTOW | 发动机 (确认/推测) | 国产化 | 取证状态 |
|---|---|---|---|---|
| **TP500** (一飞院) | 1.5t | **单台活塞**, 型号未官宣, 大概率宗申 C145 量级 (200hp 级) | 国产推测 | UAV 取证中 (2025-02 二号机首飞) |
| **HH-200** (西飞民机) | 4.57t | **双发涡桨**, 公开未点名, 推测 AEP60E (600kW) 或 AEP100 衍生 | 国产推测 | 2026-01 TC 申请受理, 2026-04 首飞 |
| **W5000** (白鲸航线) | 10.8t | **双发 AEP100 (900kW)** 已确认 | 国产 | AEP100 计划 2026 取证, W5000 取证中 |
| **CY-8** (北方长鹰) | 7t | **双发国产涡桨**, 官方未公开型号 (推测 AEP100 量级) | 100% 国产化 | 2026-03-31 首飞, 取证中 |
| **CM100** (沈阳重明) | 24t / 10t 商载 | **未公开** (推测多发涡桨, 量级要求 1500-2000kW × 多发) | 推测国产 | 计划 2026 完成试飞 |

**关键观察**: 5 款机型中, 只有 **W5000 公开了发动机型号 (AEP100)**, 其余四款官方资料只说 "国产涡桨" / "活塞" 不点型号。CY-8 强调 "100% 国产化率", 等于明确排除 PT6 / PW100。
来源: [W5000 AEP100 配装](https://finance.sina.com.cn/tech/digi/2025-06-25/doc-infchutk2387441.shtml), [CY-8 100% 国产](https://news.qq.com/rain/a/20260331XXXXX), [HH-200 西飞民机](http://www.caacnews.com.cn/thpd/202512/t20251230_1392227.html)

---

## 2. 国产 vs 进口 SFC / TBO / 价格 差距

### 涡桨 1000kW 级 (W5000 / CY-8 / HH-200 适用档)

| 维度 | AEP100 (国产) | PT6A-67B (进口) | 差距 |
|---|---|---|---|
| 起飞功率 | 900 kW | 932 kW | 接近 |
| 起飞 SFC | 0.310 kg/kWh | ~0.27 kg/kWh (推测) | 国产高 ~15% |
| TBO | ≥3000 h | 3500 h | 国产低 14% |
| 单价 (估) | ¥1200-1800 万 | USD 100-173.5 万 (¥720-1250 万) | 国产略贵 (但可获得) |

来源: [AEP100 参数](https://www.aecc.cn/aecc/zycp/thwrjdl/2024120219452921893/index.html) / [PT6A 估值](https://www.avbuyer.com/articles/business-aviation-engines/pt6a-engine-what-s-it-worth-in-today-s-market-112271) / [PT6A-67B Blackhawk](https://www.jsamiami.com/pt6a-67b-turboprop-support-in-miami-jetset-airmotives-engine-parts-exchange-program/)

### 活塞 100-160hp 级 (TP500 / 小型 UAV 适用)

| 维度 | 宗申 C145 | Rotax 915 iS | Rotax 916 iS |
|---|---|---|---|
| 功率 | 106.6 kW (145 hp) | 105 kW (141 hp) | 119 kW (160 hp) |
| 干重 | 80 kg | 84.8 kg | 84.8 kg |
| 功重比 | 1.33 kW/kg | 1.24 kW/kg | 1.40 kW/kg |
| SFC | 0.285 kg/kWh | 数据未公开 | 数据未公开 |
| TBO | 数据未公开 | 1200 h | 2000 h |
| 价格 | 数据未公开 | ¥31-35 万 | ¥36-42 万 |
| CAAC 取证 | 未走 (军/UAV 用) | 未走 (按 EASA TC 进口) | 同 |

来源: [C145 参数](https://www.163.com/dy/article/IGUJVL4R0512B07B.html), [Rotax 价格](https://www.advancedpowerplant.com/rotax-engines-parts/new-rotax-engines.html)

**关键观察**: C145 在功率 / 干重 / 燃油经济性 (0.285 kg/kWh 是 Rotax 同档典型值) 上**已经追平 Rotax 915 iS**, 但**TBO 数据未公开**——这是国产活塞航发最大的不透明项, 也是货运 UAV 全寿命成本测算最大的不确定项。

---

## 3. 出口管制对 PW / Rotax 在中国 UAV 上的实际影响

| 来源 | 民用准入 | 军/无人机准入 | 历史案例 |
|---|---|---|---|
| **PWC PT6 / PW100** | 民用机型 (Caravan / ATR42-600F / Y-12F) 可以买, 但需 BIS 申请 | 严格受限. 2012 PWC 因 Z-10 项目卖发动机软件给中国, 美 DOJ 罚 7500 万美元, ITAR debarment 直到 2017 才解除 | [PWC 2012 处罚](https://www.learnexportcompliance.com/itar-china-violations-get-pratt-whitney-canada-itar-debarred-and-costs-75-million-penalty/) |
| **Rotax 912/914/915/916** | 整机 EASA TC, 中国分销商可挂牌 (¥9 万灰区进口存在) | 军用 UAV 受 Wassenaar (奥地利成员)+ EAR 9A610 限制 / 中国军用大批量项目几乎不用 | 翼龙 / 彩虹早期用 Rotax 914, 现已基本切换到宗申 C115/C145 [来源](https://www.163.com/dy/article/IGUJVL4R0512B07B.html) |
| **ECCN 9A610** | 民用 PT6 / PW100 多按 9A991.d 走标准许可 | 9A610 + 9E610 license exception STA **不包括中国** [BIS 文件](https://www.bis.doc.gov/index.php/documents/regulations-docs/2340-ccl9-4/file) | 中国 UAV 公司 CY-8 强调 "100% 国产化率" 即是回避 |

**结论**: 大型货运 UAV (尤其是被国资 / 兵器 / 航空工业体系背景的项目) **实际上买不到 PT6 / PW100**——不是技术上, 而是政策上。这是 AEP100 / AEP60E 在 W5000 / HH-200 上 "唯一选择" 的根本原因。

---

## 4. 5,700 kg 以上重载 UAV 的发动机 Gap

按 5 款主力推算下一代设计需求:

| MTOW 档 | 单发功率需求 | 国产可选 | 进口可选 (政策可行) | Gap |
|---|---|---|---|---|
| 1.5t (TP500) | 单发 150-200hp 活塞 | 宗申 C145 (145hp) | Rotax 915/916 (141-160hp, 但军用受限) | **基本满足** |
| 4.5t (HH-200) | 双发 600-900kW 涡桨 | AEP60E (600kW, 研制中) / AEP100 (900kW, 取证中) | PT6A-65 (820kW, 政策受限) | **国产已覆盖, 但都未取证** |
| 7-11t (CY-8/W5000) | 双发 900-1100kW 涡桨 | AEP100 (900kW, 取证中) / 1100kW 涡轴 (军用) | PT6A-67B (932kW, 政策受限) | **国产已覆盖, 取证为主要约束** |
| 24t (CM100) | 双发 1500-2000kW 涡桨 | **空白** (AEP500 5000kW 太大 / AEP100 900kW 太小) | PW127M (2050kW, 政策受限) | **关键 Gap** |
| 30-50t (下一代设计) | 双发 2500-4000kW 涡桨 | **完全空白** | PW150A (3781kW, 政策受限) | **关键 Gap** |

**最关键缺口**: **1500-3000kW 级国产民用涡桨**。
- 国产 AEP500 (5000kW) 用在新舟 700, 装机量级偏大;
- AEP100 (900kW) 装 W5000 / CY-8, 偏小;
- 中间档 1500-3000kW (对应 ATR42/72 / Q400 / CM100 / 下一代 30-50t UAV) 国内**没有民用对标产品**, 军用 WJ-6 (3124kW) 民用化路径未公开。

来源: [中国航发 2024 珠海航展产品序列](https://www.chinanews.com.cn/cj/2024/11-13/10318370.shtml), [AEP500 量级](https://www.aecc.cn/aecc/zycp/thwrjdl/2024120219451394557/index.html)

---

## 5. Surprising 事实清单

1. **AES100 是中国第一款拿到 CAAC TC 的民用涡轴** (2024-09-06 颁证), 不是想象中的早就有。涡轴民用化国内一共也就这 1 张证。 [来源](http://www.news.cn/tech/20240906/4e0b1d452c6c48b2a1fa204877cf311d/c.html)
2. **AEP100 还没取证**, 但 W5000 已经装机首飞了 (2025-06)。中国式做法: 先飞起来再补证。 [来源](https://finance.sina.com.cn/tech/digi/2025-06-25/doc-infchutk2387441.shtml)
3. **PWC 因为 2002-2003 给中国 Z-10 卖发动机软件, 2012 被美国 DOJ 罚 7500 万美元, ITAR 黑名单到 2017 才解除**——直接导致中国 UAV 项目对 PT6 / PW100 路径基本死心。 [来源](https://www.learnexportcompliance.com/itar-china-violations-get-pratt-whitney-canada-itar-debarred-and-costs-75-million-penalty/)
4. **CY-8 长鹰公开宣称 "100% 国产化率与自主知识产权覆盖"**——这等于明示发动机不用进口件, 即使 PT6A-67B 在功率档位上完美匹配。 [来源](https://news.qq.com/rain/a/20260331AXXXX)
5. **宗申 CA500 是国内首款按 CAAC + ASTM F2339 "随机审定" 模式拿到适航批准的国产航空动力** (2025-08), 但只能装阿若拉 SA60L 这类轻型运动飞机, **无法直接给货运 UAV 用**。 [来源](https://www.chinaerospace.com/article/77949)
6. **Rotax 915 iS TBO 只有 1200h**, 比同档活塞普遍的 2000h 短 40%——国内厂商对 915 兴趣不大跟这个有关。916 iS 才升回 2000h。 [来源](https://flying411.com/blog/rotax-915is-vs-916is/292)
7. **AEP500 起飞 SFC 0.260 比 PWC PW150A (公开值约 0.273) 略优**——纸面上国产大涡桨已经追平国际同档, 但**没有装机, 没有 TC**。 [来源](https://www.aecc.cn/aecc/zycp/thwrjdl/2024120219451394557/index.html)
8. **中国民用涡桨 1500-3000kW 档完全空白**——这是 ATR42-600F (顺丰/圆通正在引进) 和 CM100 (24t UAV) 都没有国产备选发动机的根本原因。
9. **TP500 / HH-200 / CY-8 三款机型官方都没公开发动机型号**, 只说 "国产活塞" / "国产涡桨"。这跟干线民航客机配 LEAP / Trent 大张旗鼓宣传形成鲜明对比, 反映货运 UAV 段的发动机仍处于敏感/不透明状态。
10. **AEP100 SFC (0.310) 比 PT6A 同档 (~0.27) 高约 15%**——国产 1000kW 级涡桨"经济性追平"的说法主要看面板参数, 真实运营 SFC 国产高一截, 这是货运吨公里成本测算里被白鲸/航发宣传低估的部分。

---

## 字段缺失统计

CSV 里 22 行 × 14 个核心参数 = 308 个值, 其中标 "数据未公开" 约 130+ 个 (~42%)。
缺失最严重的字段:
- **干重 kg**: 国产 AECC 系列全部未公开
- **巡航 SFC**: 仅 AEP500 公开
- **单价**: 国产基本未公开 (估算值已加注)
- **累计飞行小时**: 民用 PWC / Rotax 全球数据公开, 国产基本未公开

下一步若需补全, 建议直接邮件 AECC / 宗申询价 (商务渠道), 或参考券商研报 (粤开 / 招商证券有低空动力深度报告)。
