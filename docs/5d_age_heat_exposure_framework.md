# 5D Built Environment Framework and Age-sensitive Urban Heat Exposure

## 中文标题

**基于 5D 建成环境框架与人口年龄结构的米兰城市热暴露空间评估研究**

## English Title

**Spatial Assessment of Urban Heat Exposure in Milan Based on the 5D Built Environment Framework and Population Age Structure**

---

## 1. Research Motivation / 研究动机

### English

The current thesis workflow already includes Land Surface Temperature (LST) and population data. However, LST and total population alone can only describe where surface heat and people are located. They are not sufficient to explain why heat exposure varies spatially, which urban characteristics amplify or reduce exposure, and which population groups are more vulnerable.

This updated framework therefore integrates two additional components:

1. **The 5D built environment framework**: Density, Diversity, Design, Destination Accessibility, and Distance to Transit.
2. **Population age structure**: children, elderly residents, and very elderly residents as heat-vulnerable groups.

The aim is to move the thesis from a simple LST-population overlay toward an interpretable urban heat exposure model with stronger theoretical support and planning relevance.

### 中文

当前毕设工作已经包括地表温度（LST）和人口数据。但仅有 LST 与总人口，只能说明“哪里热”和“哪里人多”，还不足以解释热暴露为什么在空间上存在差异、哪些城市建成环境因素会放大或缓解热暴露，以及哪些年龄群体更加脆弱。

因此，本框架在现有 LST 与人口数据基础上，进一步引入两个核心部分：

1. **5D 建成环境框架**：密度、多样性、设计、目的地可达性、到公共交通距离。
2. **人口年龄结构**：儿童、老年人、高龄老人等热脆弱群体。

研究目标是将论文从简单的 LST 与人口叠加，提升为具有理论支撑、变量解释力和规划应用价值的城市热暴露模型。

---

## 2. Conceptual Framework / 概念框架

### English

Urban heat exposure is shaped not only by land surface temperature, but also by population exposure, age-specific vulnerability, and the built environment context.

```text
Heat Risk = Thermal Hazard × Population Exposure × Age Vulnerability × Built Environment Context
```

The proposed framework contains four layers:

| Layer | Meaning | Main variables |
|---|---|---|
| Thermal Hazard | Surface heat intensity | Mean LST, P90 LST, Relative SUHI |
| Population Exposure | Number and density of exposed people | Total population, population density |
| Age Vulnerability | Heat-sensitive population structure | 0-14 ratio, 65+ ratio, 75+ ratio |
| 5D Built Environment | Urban form and accessibility context | Density, Diversity, Design, Destination Accessibility, Distance to Transit |

### 中文

城市热暴露不仅由地表温度决定，也受到人口暴露、年龄脆弱性和建成环境背景的共同影响。

```text
热风险 = 热危险性 × 人口暴露 × 年龄脆弱性 × 建成环境背景
```

本研究框架包含四个层次：

| 层次 | 含义 | 主要变量 |
|---|---|---|
| 热危险性 | 地表热强度 | 平均 LST、P90 LST、Relative SUHI |
| 人口暴露 | 暴露人口数量与密度 | 总人口、人口密度 |
| 年龄脆弱性 | 热敏感年龄结构 | 0-14 岁比例、65+ 比例、75+ 比例 |
| 5D 建成环境 | 城市形态与可达性背景 | 密度、多样性、设计、目的地可达性、到公共交通距离 |

---

## 3. Research Questions / 研究问题

### RQ1

**English:** What are the spatial patterns of LST-based urban heat exposure in Milan?

**中文：** 米兰基于 LST 的城市热暴露空间格局是什么？

### RQ2

**English:** How do 5D built environment characteristics influence the spatial distribution of urban heat exposure?

**中文：** 5D 建成环境特征如何影响米兰城市热暴露的空间分布？

### RQ3

**English:** Which age groups and urban areas are most vulnerable to heat exposure under different built environment conditions?

**中文：** 在不同建成环境条件下，哪些年龄群体和城市区域面临更高热暴露风险？

---

## 4. Recommended Spatial Unit / 推荐空间分析单元

The preferred unit depends on the resolution of available population age data.

| Spatial unit | Advantage | Limitation | Recommendation |
|---|---|---|---|
| Census section | Fine spatial detail, suitable for population analysis | More complex processing | Best option if age data are available |
| NIL | Strong local policy relevance in Milan | Coarser spatial resolution | Good option for thesis interpretation |
| 250 m grid | Suitable for raster and remote sensing variables | Population disaggregation is needed | Useful for sensitivity analysis |

**Recommended choice:** use census sections if age-structured population data are available; otherwise use NIL as a policy-oriented spatial unit.

**中文建议：** 如果可以获得 census section 级别的年龄人口数据，优先使用 census section；如果年龄结构只能到 NIL，则使用 NIL，更适合政策解释和城市规划讨论。

---

## 5. Variable System / 变量体系

### 5.1 Thermal Hazard / 热危险性

| Variable | Description | Suggested aggregation |
|---|---|---|
| Mean LST | Average surface temperature | Mean within spatial unit |
| Max LST | Maximum surface temperature | Max within spatial unit |
| P90 LST | High-end surface heat | 90th percentile within spatial unit |
| Relative SUHI | Pixel-level temperature deviation from Milan mean | Mean or P90 within spatial unit |

**Note:** P90 LST is recommended because it captures extreme local heat better than mean LST.

**说明：** 建议加入 P90 LST，因为它比平均 LST 更能代表空间单元内部的局部高温暴露。

---

### 5.2 Population Exposure / 人口暴露

| Variable | Description | Formula |
|---|---|---|
| Total population | Number of residents | Sum by spatial unit |
| Population density | Population concentration | Population / area |
| Basic heat exposure | LST-population interaction | LST × population density |
| Population-weighted LST | Temperature weighted by population | Σ(LST_i × Pop_i) / ΣPop_i |

---

### 5.3 Age Vulnerability / 年龄脆弱性

| Variable | Meaning | Role |
|---|---|---|
| 0-14 ratio | Children ratio | Heat-sensitive group |
| 65+ ratio | Elderly ratio | High-risk group |
| 75+ ratio | Very elderly ratio | Higher-risk group |
| Elderly density | Elderly population per area | Age-specific exposure intensity |
| Children density | Children population per area | Age-specific exposure intensity |

Recommended age-sensitive exposure indicators:

```text
Exposure_total_i = LST_i × Population_i
Exposure_elderly_i = LST_i × Population_65plus_i
Exposure_children_i = LST_i × Population_0_14_i
```

Standardized version:

```text
Age-sensitive Heat Vulnerability Index = z(LST) + z(Population density) + z(65+ ratio) + z(0-14 ratio)
```

---

## 6. 5D Built Environment Variables / 5D 建成环境变量

### D1. Density / 密度

Density represents the intensity of urban development and population concentration.

| Variable | 中文 | Calculation |
|---|---|---|
| Population density | 人口密度 | population / area |
| Building density | 建筑密度 | building footprint area / unit area |
| Road density | 道路密度 | road length / unit area |
| Imperviousness | 不透水面比例 | mean imperviousness or impervious area ratio |

Expected role: higher density may increase both surface heat and exposed population.

---

### D2. Diversity / 多样性

Diversity describes land-use composition and functional mixture.

| Variable | 中文 | Calculation |
|---|---|---|
| Land use mix index | 土地利用混合度 | Shannon entropy |
| Residential land ratio | 居住用地比例 | residential area / total area |
| Industrial land ratio | 工业用地比例 | industrial area / total area |
| Commercial land ratio | 商业用地比例 | commercial area / total area |
| Green-blue ratio | 蓝绿空间比例 | green + water area / total area |

Land use mix formula:

```text
LUM_i = -Σ(p_k × ln p_k) / ln(K)
```

where `p_k` is the area share of land-use class k in spatial unit i, and K is the number of land-use classes.

---

### D3. Design / 设计与城市形态

Design describes local spatial configuration of streets, buildings, and green-blue infrastructure.

| Variable | 中文 | Calculation |
|---|---|---|
| NDVI | 植被指数 | mean NDVI |
| Tree cover density | 树冠覆盖率 | mean tree cover percentage |
| Intersection density | 路口密度 | intersections / area |
| Block size | 街区尺度 | mean block area |
| Distance to water | 到水体距离 | nearest distance |
| Green fragmentation | 绿地破碎度 | patch density or edge density |

Expected role: vegetation and tree cover reduce heat exposure, while poor street design or fragmented green spaces may weaken cooling capacity.

---

### D4. Destination Accessibility / 目的地可达性

Destination accessibility evaluates whether residents in hot areas can access cooling and supportive resources.

| Variable | 中文 | Calculation |
|---|---|---|
| Distance to nearest park | 到最近公园距离 | nearest distance |
| Park area within 500 m | 500 米范围内公园面积 | buffer statistics |
| Green space accessibility | 绿地可达性 | distance or catchment area |
| Distance to hospital / clinic | 到医疗设施距离 | nearest distance |
| Cooling facility accessibility | 避暑设施可达性 | distance to libraries, public buildings, civic centers |

Age-linked accessibility example:

```text
Elderly Cooling Accessibility Gap = Elderly population density × Distance to nearest park
```

This identifies areas with many elderly residents but poor access to cooling resources.

---

### D5. Distance to Transit / 到公共交通距离

This dimension captures potential outdoor exposure related to commuting, waiting, and transfer activities.

| Variable | 中文 | Calculation |
|---|---|---|
| Distance to metro station | 到地铁站距离 | nearest distance |
| Distance to bus/tram stop | 到公交/电车站距离 | nearest distance |
| Transit stop density | 站点密度 | stops / area |
| Transit heat exposure | 交通节点热暴露 | mean LST within station buffer |
| Elderly transit exposure | 老年人交通热暴露 | elderly density × station-buffer LST |

---

## 7. Minimum Viable Variable Set / 最小可行变量集

For a feasible master thesis, the first version can use approximately 10 variables:

```text
LST
Population density
65+ ratio
0-14 ratio
NDVI
Imperviousness
Land use mix
Building density
Distance to nearest park
Distance to nearest transit stop
```

This set covers thermal hazard, population exposure, age vulnerability, and all five 5D dimensions.

---

## 8. Suggested Indices / 推荐指数构建

### 8.1 Total Heat Exposure Index / 总人口热暴露指数

```text
Total Heat Exposure Index = z(LST) + z(Population density)
```

### 8.2 Age-sensitive Heat Vulnerability Index / 年龄敏感型热脆弱性指数

```text
Age-sensitive Heat Vulnerability Index =
z(LST) + z(Population density) + z(65+ ratio) + z(0-14 ratio)
```

### 8.3 5D Age-sensitive Heat Risk Index / 5D 年龄敏感型热风险指数

```text
5D Age-sensitive Heat Risk Index =
z(LST)
+ z(Population density)
+ z(65+ ratio)
+ z(0-14 ratio)
+ z(Imperviousness)
+ z(Building density)
+ z(Road density)
+ z(Industrial land ratio)
- z(NDVI)
- z(Tree cover density)
- z(Park area within 500m)
+ z(Distance to nearest park)
```

General structure:

```text
Risk_i = Hazard_i + Exposure_i + Vulnerability_i + Urban Amplifier_i - Cooling Capacity_i
```

---

## 9. Methodological Workflow / 方法路线

### Step 1. Prepare thermal hazard layers / 准备热危险性图层

- Process Landsat LST for Milan.
- Generate mean LST, P90 LST, and Relative SUHI.
- Clip all results to the official Comune di Milano boundary.

### Step 2. Prepare population and age structure / 准备人口与年龄结构数据

- Collect total population and age groups.
- Calculate population density, elderly ratio, children ratio, elderly density, and children density.
- Match all population variables to the selected spatial unit.

### Step 3. Prepare 5D built environment variables / 准备 5D 建成环境变量

- Density: building density, road density, imperviousness.
- Diversity: land-use mix, industrial ratio, green-blue ratio.
- Design: NDVI, tree cover, intersection density.
- Destination Accessibility: distance to parks, park area within 500 m.
- Distance to Transit: distance to metro/bus/tram stops, transit stop density.

### Step 4. Spatial aggregation / 空间聚合

Aggregate all raster, vector, and point variables to the same spatial unit.

| Data type | Aggregation method |
|---|---|
| LST | mean, max, P90 |
| Population | sum, density |
| Age groups | age group count / total population |
| NDVI | mean |
| Imperviousness | mean or percentage |
| Land use | area percentage |
| Buildings | footprint area percentage |
| Roads | length density |
| Parks | distance or buffer area |
| Transit | distance or stop density |

### Step 5. Index construction and modelling / 指数构建与模型分析

Recommended analysis routes:

1. **Index-based mapping**: robust and easy to explain.
2. **OLS regression**: basic statistical explanation.
3. **Random Forest**: nonlinear variable importance.
4. **GWR**: spatial heterogeneity if time allows.
5. **SHAP interpretation**: variable contribution for machine-learning models.

---

## 10. Expected Outputs / 预期成果图

Recommended maps and outputs:

1. LST spatial distribution map.
2. Relative SUHI map.
3. Population density map.
4. Elderly ratio map.
5. Children ratio map.
6. NDVI or green space map.
7. Imperviousness map.
8. 5D built environment variable maps.
9. Total heat exposure hotspot map.
10. Elderly heat exposure hotspot map.
11. Children heat exposure hotspot map.
12. Heat adaptation priority map.

The most important final output is the **Heat Adaptation Priority Map**, which identifies areas with high temperature, high population exposure, high age vulnerability, and weak cooling accessibility.

---

## 11. Thesis Structure / 论文结构建议

### Chapter 1. Introduction

- Urban heat exposure background.
- Milan as the case study.
- Limitations of LST-only exposure mapping.
- Rationale for integrating 5D and age structure.
- Research questions and contributions.

### Chapter 2. Literature Review

- Urban heat exposure.
- LST and SUHI.
- Population vulnerability and age-specific heat risk.
- 5D built environment framework.
- Environmental justice and spatial inequality.

### Chapter 3. Data and Methods

- Study area.
- LST processing.
- Population and age structure data.
- 5D variable construction.
- Spatial aggregation.
- Index construction and modelling methods.

### Chapter 4. Results

- LST and SUHI spatial patterns.
- Age distribution patterns.
- 5D built environment patterns.
- Total and age-specific heat exposure.
- Model results and variable importance.
- Heat adaptation priority areas.

### Chapter 5. Discussion

- Interpretation of important 5D variables.
- Age-specific vulnerability patterns.
- Planning implications for green infrastructure and cooling accessibility.
- Methodological limitations.

### Chapter 6. Conclusion

- Main findings.
- Methodological contribution.
- Policy and planning implications.
- Future research directions.

---

## 12. Short Explanation for Supervisor / 给导师的简短说明

### English

Based on the current LST and population datasets, I plan to integrate the 5D built environment framework and population age structure to develop an age-sensitive urban heat exposure assessment model. The 5D framework, including density, diversity, design, destination accessibility, and distance to transit, will be used to explain how built environment characteristics shape heat exposure. Population age structure will be used to identify vulnerable groups such as older adults and children. The final output will include heat exposure indices for the total population, elderly population, and children, as well as priority areas for heat adaptation in Milan.

### 中文

我计划在现有 LST 和人口数据的基础上，引入 5D 建成环境框架和人口年龄结构，构建一个年龄敏感型城市热暴露评估模型。5D 框架包括密度、多样性、城市设计、目的地可达性和公共交通距离，用于解释城市形态如何影响热暴露；年龄结构则用于识别老年人和儿童等热脆弱群体。最终我会构建总人口、老年人和儿童的热暴露指数，并识别米兰需要优先进行热适应干预的区域。
