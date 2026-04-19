# 数据源档案

本目录存放 index.html 中所有图表使用的原始数据，方便逐项核对数据来源和准确性。

## 核对方法

每个 CSV 文件对应一个 section，每行一个数据点，包含字段：
- **当前值** (current_value)：index.html 中实际使用的数字
- **字段含义** (field_meaning)：这个数字代表什么
- **单位** (unit)：单位说明
- **数据源 URL** (source_url)：引用的网站链接
- **原始源** (primary_source)：数据最终来源机构（即使是从 Wikipedia 爬的，也要写原始源）
- **数据年份** (vintage)：这个数字对应哪一年的数据
- **采集方式** (method)：官方年鉴 / Wikipedia / 研报估算 / 原作者估算 / 待验证
- **状态** (status)：verified / unverified / needs_update / conflict
- **备注** (notes)：已知问题、偏差、替代值等

## 当前文件列表

| 文件 | 对应 section | 内容 |
|------|--------------|------|
| s1_cn_provinces.csv | S1 地理与经济 | 中国 34 省市自治区: 人口密度、人均 GDP、通航机场数、面积、人口 |
| s1_us_states.csv | S1 地理与经济 | 美国 50 州 + DC: 同上 |
| s1_cn_airports.csv | S1 地图散点 | 中国 40 个主要机场: 坐标、类型、货运量 |
| s1_us_airports.csv | S1 地图散点 | 美国 45 个主要机场: 同上 |
| s1_cargo_hubs.csv | S1 公路辐射覆盖 | 中国 10 大 + 美国 10 大货运枢纽坐标 |

## 已知数据问题（未修复）

1. **中美 GDP 数据年份不一致**: 中国约 2022-2023 vintage, 美国约 2021-2022 vintage
2. **美国州人口单位混乱**: data 中 pop 字段是"千人"但 JS 代码 (line 2058) 按"万人"计算 → 美国州"机场/百万人"被系统性低估 10 倍
3. **source 标签写"2024"但实际数据是旧年份**: 属于标注错误
4. **CAAC 通航机场总数 475**: 已标注为 2024.12, 但需要复核是 NPIAS 口径对等还是只是 CAAC 颁证的民用机场

## 工作流

用户逐个 section 检查数据时:
1. 用户提出具体数据点的质疑（例如 "北京人均 GDP 应该是 X"）
2. Claude 更新 CSV 的 current_value + notes
3. 确认后 Claude 同步更新 index.html 中的 JS 数据
4. source 标签同步更新为 primary_source + URL
