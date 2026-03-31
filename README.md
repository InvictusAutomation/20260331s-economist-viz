# 📊 Economist 可视化 + AI 动态图表

基于《经济学人》风格的动态可视化工具，结合 amis 低代码框架实现 AI 实时数据驱动的图表渲染。

## 🎯 核心功能

1. **Economist 风格图表** - 经典经济学人可视化风格复刻
2. **Amis 低代码** - 通过 JSON 配置生成图表
3. **AI 实时驱动** - Agent 实时组织数据，动态渲染图表

## 🚀 快速开始

### 方式一：直接运行演示（推荐）

```bash
# 进入演示目录
cd demo

# 启动 HTTP 服务器
python3 -m http.server 8080
# 或
npx serve .
```

打开浏览器访问：http://localhost:8080

### 方式二：完整的 Amis 开发环境

```bash
# 1. 克隆仓库
git clone https://github.com/InvictusAutomation/20260331s-economist-viz.git
cd 20260331s-economist-viz

# 2. 安装依赖
npm install echarts

# 3. 运行演示
cd demo && python3 -m http.server 8080
```

### 方式三：完整的 Amis 开发服务器

```bash
# 1. 安装 Node.js (12/14/16)
# 下载: https://nodejs.org

# 2. 克隆百度 amis
git clone https://github.com/baidu/amis.git
cd amis

# 3. 安装依赖
npm i --legacy-peer-deps

# 4. 启动开发服务器
npm start
# 访问: http://127.0.0.1:8888/examples/pages/simple
```

## 📦 依赖

- [amis](https://github.com/baidu/amis) - 百度低代码框架
- [echarts](https://github.com/apache/echarts) - 图表库
- [aendra-rininsland/economist](https://github.com/aendra-rininsland/economist) - 经济学人风格

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

### 房价趋势图（API 驱动）

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

### 完整示例

```html
<!DOCTYPE html>
<html>
<head>
    <script src="https://cdn.jsdelivr.net/npm/echarts@5.4.3/dist/echarts.min.js"></script>
</head>
<body>
    <div id="chart" style="width:800px;height:400px;"></div>
    <script>
        const chart = echarts.init(document.getElementById('chart'));
        const option = {
            title: { text: 'Economist 风格图表' },
            color: ['#014D45'],
            xAxis: { type: 'category', data: ['Q1','Q2','Q3','Q4'] },
            yAxis: { type: 'value' },
            series: [{ type: 'line', data: [30, 45, 60, 55] }]
        };
        chart.setOption(option);
    </script>
</body>
</html>
```

## 🎨 Economist 主题

### 配色方案

```javascript
const economistTheme = {
    primary: '#014D45',   // 深绿色
    red: '#E60000',       // 红色
    yellow: '#FFD100',    // 黄色
    orange: '#FF7E00',    // 橙色
    background: '#FFFFFF',
    text: '#333333'
};
```

### 主题特征

- 深绿色为主色调 (#014D45)
- 简洁的网格线
- 平滑的面积填充
- 清晰的标题布局

## 🤖 AI 集成

### 实时数据获取

```javascript
// 通过 Agent 获取实时数据
async function fetchAIData(prompt) {
    const response = await fetch('/api/agent', {
        method: 'POST',
        body: JSON.stringify({ prompt })
    });
    return response.json();
}

// 使用
const data = await fetchAIData('获取最近��周的房价趋势');
chart.setOption({ series: [{ data: data.values }] });
```

### 数据源

- 本地 JSON 文件
- REST API
- WebSocket 实时推送
- AI Agent 动态生成

## 📁 项目结构

```
economist-viz/
├── demo/
│   └── index.html      # 演示页面
├── docs/
│   ├── configuration # 配置文档
│   └── themes        # 主题文件
└── README.md
```

## 🔗 参考仓库

| 仓库 | 描述 |
|------|------|
| [baidu/amis](https://github.com/baidu/amis) | 百度低代码框架 |
| [aendra-rininsland/economist](https://github.com/aendra-rininsland/economist) | 经济学人可视化 |
| [holtzy/R-graph-gallery](https://github.com/holtzy/R-graph-gallery) | R 图表库 (737 ⭐) |
| [clibassi/python-packages-for-applied-economists](https://github.com/clibassi/python-packages-for-applied-economists) | 经济学者 Python 工具 |

## 📜 License

MIT
