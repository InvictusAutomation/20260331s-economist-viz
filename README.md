# 📊 Economist 可视化 + AI 动态图表

基于《经济学人》风格的动态可视化工具，结合 amis 低代码框架实现 AI 实时数据驱动的图表渲染。

## 🎯 核心功能

1. **Economist 风格图表** - 经典经济学人可视化风格复刻
2. **Amis 低代码** - 通过 JSON 配置生成图表
3. **AI 实时驱动** - Agent 实时组织数据，动态渲染图表

## 🏗️ 架构

```
├── economist-theme/     # 经济学人风格
├── amis-charts/      # amis 图表组件
├── agent-connector/  # Agent 数据连接
└── demo/            # 示例
```

## 🔧 Amis 图表配置

### 基础折线图

```json
{
  "type": "chart",
  "chartData": {
    "labels": ["Jan", "Feb", "Mar"],
    "datasets": [{"data": [10, 25, 30]}]
  },
  "options": {
    "type": "line",
    "theme": "economist"
  }
}
```

### 房价趋势图

```json
{
  "type": "amis-chart",
  "api": "/api/house-prices",
  "chartType": "line",
  "theme": "economist",
  "xAxis": "date",
  "yAxis": "price"
}
```

## 🚀 运行

```bash
# 安装依赖
npm i

# 启动开发服务器
npm start
```

访问 http://127.0.0.1:8888/examples/pages/simple

## 📦 依赖

- [amis](https://github.com/baidu/amis) - 低代码框架
- [economist-viz](https://github.com/aendra-rininsland/economist) - 经济学人风格
- ECharts - 图表库

## 🔗 参考仓库

- baidu/amis
- aendra-rininsland/economist
- holtzy/R-graph-gallery
