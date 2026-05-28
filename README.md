# AI数字员工租赁平台

> 55 种专业 AI 数字员工，覆盖 2721 个业务模型，助力企业全场景智能化升级。

## 在线访问

**[https://zjgulai.github.io/ai-digital-person/](https://zjgulai.github.io/ai-digital-person/)**

## 功能概览

平台提供按需租赁的 AI 数字员工，每位员工均具备深度专业知识与完整业务流程覆盖：

| 职能领域 | 代表角色 | 模型数量 |
|---|---|---|
| 战略与管理 | 战略/管理咨询师 | 171 |
| 数据与算法 | 数据科学家/算法工程师 | 306 |
| 市场与营销 | 市场营销总监 | 数十种营销模型 |
| 财务与法务 | 财务分析师、法律顾问 | — |
| 运营与产品 | 运营分析总监、产品经理 | — |
| … | 共 55 种角色 | 合计 2721 模型 |

## 技术栈

- **前端框架**: React + Vite
- **样式**: Tailwind CSS
- **部署**: GitHub Pages（静态站点）

## 数据说明

角色与模型数据位于 [`data/roles.json`](data/roles.json)，包含：
- 55 个专业角色
- 2721 个业务模型
- 每个角色的业务流程（biz_flows）及对应分析框架

## 本地预览

```bash
# 直接用任意静态服务器预览（无需 Node.js 构建）
npx serve .
# 或
python3 -m http.server 8080
```

## 目录结构

```
├── index.html          # 入口页面
├── assets/
│   ├── index-*.js      # 主 JS bundle
│   └── index-*.css     # 主样式
├── data/
│   └── roles.json      # 角色与模型数据
└── .nojekyll           # 禁用 Jekyll 处理（GitHub Pages 必须）
```

## 许可

Copyright © 2026 路特团队. All rights reserved.
