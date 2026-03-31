---
name: amis-dashboard
description: 基于百度 amis 的动态看板生成工具 - 通过 JSON 配置生成实时数据图表
metadata:
  {
    "openclaw": { "emoji": "📊", "requires": { "anyBools": ["browser"] } },
  }
---

# Amis 动态看板生成器

_基于百度 amis 低代码框架，通过 JSON 配置生成实时数据驱动的动态图表看板。_

## 安装

```bash
# 克隆仓库
git clone https://github.com/InvictusAutomation/20260331s-economist-viz.git
cd 20260331s-economist-viz

# 安装依赖
npm install echarts
```

## 快速开始

### 启动看板

```bash
cd demo
python3 -m http.server 8080
```

打开 http://localhost:8080 查看演示。

### 创建新图表

1. 准备数据源 (API 或 JSON)
2. 编写 Amis JSON 配置
3. 渲染到页面

## 使用方法

### 基本命令

```bash
# 启动开发服务器
/start

# 查看示例
/examples

# 创建新图表
/create "图表名称"
```

### 创建动态看板

```
用户: 帮我创建一个显示月度销售额的看板

Skill: 
1. 解析需求 (月度销售额)
2. 准备数据 JSON
3. 生成 Amis 配置
4. 展示结果
```

## Amis 图表配置范式

### 1. 折线图

```json
{
  "type": "chart",
  "chartData": {
    "labels": ["1月", "2月", "3月", "4月", "5月", "6月"],
    "values": [120, 145, 180, 165, 200, 220]
  },
  "options": {
    "type": "line",
    "theme": "economist",
    "title": "月度销售额趋势",
    "xAxis": "月份",
    "yAxis": "销售额(万)",
    "smooth": true,
    "areaStyle": true
  }
}
```

### 2. 柱状图

```json
{
  "type": "chart",
  "chartData": {
    "labels": ["产品A", "产品B", "产品C", "产品D"],
    "values": [4500, 3200, 2800, 5100]
  },
  "options": {
    "type": "bar",
    "theme": "economist",
    "title": "产品销售额",
    "color": "#014D45"
  }
}
```

### 3. 散点图

```json
{
  "type": "chart",
  "chartData": {
    "data": [
      [10, 20], [15, 45], [25, 30], [30, 60],
      [40, 50], [45, 80], [50, 35], [55, 75]
    ]
  },
  "options": {
    "type": "scatter",
    "title": "价格与销量关系",
    "xAxis": "价格",
    "yAxis": "销量"
  }
}
```

### 4. 饼图

```json
{
  "type": "chart",
  "chartData": {
    "labels": ["华东区", "华南区", "华北区", "西区"],
    "values": [35, 25, 20, 20]
  },
  "options": {
    "type": "pie",
    "title": "区域销售占比",
    "colors": ["#014D45", "#E60000", "#FFD100", "#FF7E00"]
  }
}
```

### 5. 动态仪表盘

```json
{
  "type": "chart",
  "api": "/api/realtime-sales",
  "options": {
    "type": "gauge",
    "title": "实时销售额",
    "min": 0,
    "max": 100000,
    "theme": "economist"
  }
}
```

## 数据源配置

### 本地数据

```json
{
  "type": "chart",
  "data": {
    "source": "local",
    "values": [...]
  }
}
```

### API 数据

```json
{
  "type": "chart",
  "api": {
    "url": "/api/data",
    "method": "GET",
    "interval": 5000  // 5秒刷新
  }
}
```

### 数据库 (待对接公司数据)

```json
{
  "type": "chart",
  "api": {
    "url": "/api/db",
    "source": "company-db",
    "query": "SELECT * FROM sales"
  }
}
```

## 主题配置

### Economist 风格

```json
{
  "theme": "economist",
  "colors": {
    "primary": "#014D45",
    "secondary": "#E60000",
    "accent": "#FFD100"
  },
  "grid": {
    "show": true,
    "color": "#E5E5E5"
  }
}
```

### 自定义主题

```json
{
  "theme": {
    "primary": "#2d5a47",
    "background": "#f5f5f5",
    "text": "#333333"
  }
}
```

## 生成流程

```
1. 接收需求
   ↓
2. 解析数据类型 (销售/库存/用户/财务)
   ↓
3. 选择图表类型 (折线/柱状/饼/仪表盘)
   ↓
4. 编写 Amis JSON 配置
   ↓
5. 渲染并展示
```

## 示例

### 示例 1: 销售仪表盘

```bash
/create dashboard sales
```

生成包含以下图表的销售仪表盘：
- 月度销售趋势 (折线图)
- 产品分类占比 (饼图)
- 区域销售排名 (柱状图)
- 实时销售仪表盘 (仪表盘)

### 示例 2: 用户分析

```bash
/create chart user-growth
```

生成用户增长趋势图。

### 示例 3: 财务报告

```bash
/create financial-report
```

生成财务相关图表。

## 对接公司数据库

当用户配置公司数据库后，可以使用：

```json
{
  "type": "chart",
  "api": {
    "source": "company-db",
    "port": 3306,
    "database": "company_db",
    "query": "SELECT date, amount FROM sales WHERE ..."
  }
}
```

## 参考

- [amis 官方文档](https://aisuda.github.io/amis-docs/)
- [ECharts 文档](https://echarts.apache.org/)
- [Economist Visualization](https://github.com/aendra-rininsland/economist)
