# AI 数字员工租赁平台（发布产物仓库）

> 55 种专业 AI 数字员工，覆盖 2721 个业务模型，助力企业战略、数据分析、营销、法律、财务等全场景智能化升级。

> ⚠️ **本仓库存放的是构建产物（dist），不是源码。**
> 源码项目位于：`/Users/lute/project/Agent/product/ai_employ_platform_src/`
> 所有 UI 修改、功能迭代请在源码项目中进行，build 后将 `dist/` 同步到本仓库。

---

## 在线访问

| 环境 | 地址 | 说明 |
|---|---|---|
| **生产（腾讯云）** | [https://person.lute-tlz-dddd.top](https://person.lute-tlz-dddd.top) | 主部署，nginx + TLS，长期稳定 |
| **GitHub Pages** | [https://zjgulai.github.io/ai-digital-person/](https://zjgulai.github.io/ai-digital-person/) | 备用/演示，推送 main 自动更新 |
| **宿主导航页** | [https://lute-tlz-dddd.top](https://lute-tlz-dddd.top) | 路特平台入口，已展示本项目卡片 |

---

## 功能概览

平台提供按需租赁的 AI 数字员工，每位员工均具备深度专业知识与完整业务流程覆盖。

### 55 种专业角色（完整列表）

| # | 角色 | # | 角色 | # | 角色 |
|---|---|---|---|---|---|
| 1 | 战略/管理咨询师 | 20 | 哲学专家 | 39 | 直播运营 |
| 2 | 数据科学家/算法工程师 | 21 | 个人成长导师 | 40 | 私域运营 |
| 3 | 运营分析总监 | 22 | 前端开发工程师 | 41 | SEO/SEM优化师 |
| 4 | 思维与认知专家 | 23 | Java后端工程师 | 42 | 品牌经理 |
| 5 | 产品经理 | 24 | Python开发工程师 | 43 | 销售经理 |
| 6 | 市场/增长负责人 | 25 | 测试工程师/QA | 44 | 商务拓展/BD |
| 7 | 沟通提问大师 | 26 | 运维工程师/SRE | 45 | 财务分析师 |
| 8 | 金融量化分析师 | 27 | 网络安全工程师 | 46 | 项目经理/PMP |
| 9 | 医疗数据分析师 | 28 | 云计算架构师 | 47 | 碳资产管理师 |
| 10 | 供应链专家 | 29 | 数据库工程师/DBA | 48 | ESG分析师 |
| 11 | 人力资源专家 | 30 | UI设计师 | 49 | 保险精算师 |
| 12 | 软件工程师/架构师 | 31 | UX设计师 | 50 | 风控建模师 |
| 13 | 法律分析师 | 32 | AIGC工程师 | 51 | 游戏策划师 |
| 14 | 环境科学家 | 33 | Prompt工程师 | 52 | 跨境电商运营 |
| 15 | 教育专家 | 34 | 增长产品经理 | 53 | 营养师 |
| 16 | 通用分析师 | 35 | 数据产品经理 | 54 | 旅游规划师 |
| 17 | 自媒体专家 | 36 | 内容运营 | 55 | 宠物行业专家 |
| 18 | 社会学专家 | 37 | 社群运营 | | |
| 19 | 心理学专家 | 38 | 电商运营 | | |

### 数据统计

- **角色总数**：55 种
- **业务模型总数**：2721 个（已去重）
- **单角色业务流程数**：3 ~ 31 个
- **定价示例**（战略/管理咨询师）：基础版 ¥299 / 专业版 ¥599 / 企业版 ¥1299

> 完整的业务流程（biz_flows）与业务模型（models）详见 [`data/roles.json`](data/roles.json)。

---

## 技术栈

| 层次 | 技术 |
|---|---|
| 前端框架 | React 19 + TypeScript + Vite 5 |
| 样式 | Tailwind CSS v3 + CSS 变量主题系统 |
| 路由 | React Router DOM v7 |
| 图标 | lucide-react |
| 数据层 | 静态 JSON（`data/roles.json`，55 角色 × 2721 模型） |
| 生产部署 | Nginx（复用 `ai_video_nginx` 容器）+ Let's Encrypt TLS |
| 备用部署 | GitHub Pages（`main` 分支自动发布） |

---

## 仓库说明：产物 vs 源码

本仓库（`ai_employ_platform`）存放的是 **Vite 构建后的 dist 产物**，用于直接部署：

```
ai_employ_platform/           ← 本仓库（发布产物）
├── index.html                # 入口 HTML
├── assets/
│   ├── index-Bea_gqK8.js    # 主 JS bundle（~290 KB）
│   └── index-BIlXnRl6.css   # 主样式（~20 KB，含完整 Tailwind）
├── data/
│   └── roles.json            # 55 角色 × 2721 模型数据
├── favicon.svg / icons.svg   # 图标资源
├── .gitignore                # 排除 *.pem / .DS_Store
├── .nojekyll                 # GitHub Pages 必须
└── ai_video.pem              # SSH 私钥（永不提交）
```

源码项目（二次开发请在此操作）：

```
/Users/lute/project/Agent/product/ai_employ_platform_src/   ← 源码项目
├── src/
│   ├── types/index.ts           # TypeScript 类型定义
│   ├── data/
│   │   ├── roleDetails.ts       # 角色详情数据（7个完整 + 通用模板）
│   │   └── pricingPlans.ts      # 定价方案 + FAQ
│   ├── lib/dataService.ts       # roles.json 加载 + 缓存
│   ├── components/              # Navbar / Footer / BackToTop
│   ├── sections/                # Hero / Benefits / HowItWorks / TopRoles / CTA
│   └── pages/                   # Home / Marketplace / RoleDetail / Pricing / About
├── public/data/roles.json       # 开发时数据（与 dist 同步）
├── postcss.config.mjs           # ⚠️ .mjs 格式（Node 26 + ESM 兼容）
├── tailwind.config.js
└── vite.config.ts
```

> ⚠️ **Node 兼容性注意**：本项目使用 Node v26.0.0。须用 Vite 5（不兼容 Vite 8）。
> PostCSS 配置必须是 `postcss.config.mjs`（ESM 格式），不能是 `.js` 或 `.cjs`。

---

## 部署架构

### 生产环境（腾讯云 101.34.52.232 / VM-0-16-ubuntu）

```
                Internet
                    │ :80 / :443
          ┌─────────▼──────────────┐
          │     ai_video_nginx     │  ← 共享 nginx 容器（所有域名复用）
          │     nginx:alpine       │
          └──────────┬─────────────┘
                     │ bind mount :ro
      ┌──────────────▼──────────────────────┐
      │  /opt/ai-employ-platform/html/       │
      │  ├── index.html                      │
      │  ├── assets/index-CuBuKeQA.js        │
      │  ├── assets/index-xamrtRg3.css       │
      │  └── data/roles.json                 │
      └──────────────────────────────────────┘
```

**关键文件位置（服务器上）**

| 内容 | 路径 |
|---|---|
| 静态文件根目录 | `/opt/ai-employ-platform/html/` |
| nginx 主配置 | `/opt/ai-video/deploy/lighthouse/nginx.conf` |
| docker-compose | `/opt/ai-video/deploy/lighthouse/docker-compose.prod.yml` |
| SSL 证书 | `/etc/letsencrypt/live/lute-tlz-dddd.top/`（到期 2026-08-26） |
| nginx 容器名 | `ai_video_nginx` |
| 宿主导航页 | `/opt/ai-video/deploy/lighthouse/landing/index.html` |

**nginx 配置要点（`nginx.conf` 中的 person 段）**

```nginx
server {
    listen 443 ssl;
    http2 on;
    server_name person.lute-tlz-dddd.top;
    ssl_certificate /etc/letsencrypt/live/lute-tlz-dddd.top/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/lute-tlz-dddd.top/privkey.pem;
    root /var/www/person;       # 容器内路径
    index index.html;
    location / { try_files $uri $uri/ /index.html; }
    location /data/ { add_header Cache-Control "public, max-age=3600"; }
    location ~* \.(js|css|...)$ { add_header Cache-Control "public, max-age=604800, immutable"; }
}
```

**docker-compose volume mount（`docker-compose.prod.yml` nginx 段末尾）**

```yaml
- /opt/ai-employ-platform/html:/var/www/person:ro
```

### GitHub Pages（备用）

仓库 `zjgulai/ai-digital-person`，`main` 分支根目录，推送即自动部署（约 30-60 秒生效）。

---

## 二次开发标准流程

**所有 UI / 功能改动都在源码项目进行，禁止直接修改产物文件。**

```bash
# Step 1：进入源码目录
cd /Users/lute/project/Agent/product/ai_employ_platform_src

# Step 2：开发（热重载预览）
npm run dev         # 访问 http://localhost:5173

# Step 3：构建
npm run build       # 产物输出到 dist/

# Step 4：同步产物到本仓库（发布产物）
rsync -av --delete dist/ /Users/lute/project/Agent/product/ai_employ_platform/
# 注意：排除 .git/ .gitignore .nojekyll ai_video.pem README.md
# 实际执行时加 --exclude 或手动复制 assets/ data/ index.html

# Step 5：同步到生产服务器
rsync -avz --delete \
  -e "ssh -i /path/to/ai_video.pem" \
  dist/ \
  ubuntu@101.34.52.232:/opt/ai-employ-platform/html/

# Step 6：推送到 GitHub（同步 GitHub Pages）
git add assets/ data/ index.html
git commit -m "feat: <描述>"
git push origin main
```

> 详细开发说明见源码项目：`/Users/lute/project/Agent/product/ai_employ_platform_src/README.md`
> 产品迭代路线图见：`/Users/lute/project/Agent/product/ai_employ_platform_src/ROADMAP.md`

---

## 运维手册

### 更新静态文件（最常见操作）

```bash
# 本地修改完成后，rsync 同步到服务器
rsync -avz \
  -e "ssh -i ai_video.pem" \
  index.html assets/ data/ \
  ubuntu@101.34.52.232:/opt/ai-employ-platform/html/

# nginx bind mount，文件替换后浏览器刷新即生效，无需 reload nginx
```

### 更新 roles.json 数据

```bash
# 1. 修改 data/roles.json 后，先做去重验证
python3 -c "
import json
with open('data/roles.json') as f:
    d = json.load(f)
for role in d['roles']:
    for flow in role['biz_flows']:
        seen = set()
        for m in flow['models']:
            key = (m['name'], m['type'], m['category'])
            assert key not in seen, f'重复: {key} in {role[\"name\"]}/{flow[\"name\"]}'
            seen.add(key)
print('验证通过，角色数:', d['total_roles'], '，模型数:', d['total_models'])
"

# 2. 同步到服务器
rsync -avz -e "ssh -i ai_video.pem" \
  data/roles.json \
  ubuntu@101.34.52.232:/opt/ai-employ-platform/html/data/

# 3. 同步到 GitHub
git add data/roles.json && git commit -m "data: 更新角色数据" && git push
```

### 同步到 GitHub Pages

```bash
git add .
git commit -m "feat/fix: <描述>"
git push origin main
# 约 30-60 秒后 https://zjgulai.github.io/ai-digital-person/ 自动更新
```

### SSL 证书（certbot 自动续期，通常无需手动操作）

```bash
# 查看证书状态
ssh -i ai_video.pem ubuntu@101.34.52.232 "sudo certbot certificates"

# 如需 expand 新子域名（需列出所有已有域名 + 新域名）
ssh -i ai_video.pem ubuntu@101.34.52.232 "sudo certbot certonly \
  --webroot -w /var/www/certbot --expand \
  -d lute-tlz-dddd.top \
  -d business.lute-tlz-dddd.top -d kg.lute-tlz-dddd.top \
  -d mkt.lute-tlz-dddd.top -d person.lute-tlz-dddd.top \
  -d report.lute-tlz-dddd.top -d shopify.lute-tlz-dddd.top \
  -d video.lute-tlz-dddd.top -d voc.lute-tlz-dddd.top \
  -d <新域名> \
  --non-interactive --agree-tos"
```

### nginx 配置变更流程

```bash
# 1. 备份
ssh -i ai_video.pem ubuntu@101.34.52.232 "
  TS=\$(date +%Y%m%d_%H%M%S)
  cp /opt/ai-video/deploy/lighthouse/nginx.conf \
     /opt/ai-video/deploy/lighthouse/nginx.conf.bak_\${TS}"

# 2. 在宿主机编辑 /opt/ai-video/deploy/lighthouse/nginx.conf

# 3. 语法验证（在运行容器内，upstream DNS 可用）
ssh -i ai_video.pem ubuntu@101.34.52.232 "
  docker cp /opt/ai-video/deploy/lighthouse/nginx.conf \
    ai_video_nginx:/tmp/nginx_test.conf
  docker exec ai_video_nginx nginx -t -c /tmp/nginx_test.conf"

# 4. 热 reload（零停机，仅修改 nginx.conf 时使用）
ssh -i ai_video.pem ubuntu@101.34.52.232 \
  "docker exec ai_video_nginx nginx -s reload"

# ⚠️ 如果新增了 volume mount，需重建容器（约 3s 中断）：
# cd /opt/ai-video/deploy/lighthouse
# docker compose -f docker-compose.prod.yml up -d --no-deps --force-recreate nginx
```

### 验证所有站点健康

```bash
ssh -i ai_video.pem ubuntu@101.34.52.232 "
  for url in \
    https://person.lute-tlz-dddd.top/ \
    https://video.lute-tlz-dddd.top/ \
    https://voc.lute-tlz-dddd.top/ \
    https://kg.lute-tlz-dddd.top/ \
    https://report.lute-tlz-dddd.top/ \
    https://business.lute-tlz-dddd.top/; do
    code=\$(curl -s -o /dev/null -w '%{http_code}' \"\$url\")
    echo \"\$code  \$url\"
  done"
```

---

## 二次开发指南

### 场景一：新增 / 修改角色数据

1. 编辑 `data/roles.json`（注意同步修正 `model_count` 和 `biz_flow_count` 字段）
2. 运行去重验证脚本（见上）
3. `rsync` 同步到服务器 + `git push` 同步到 GitHub

### 场景二：前端 UI 需要修改

本仓库存放的是**预构建产物**（Vite dist）。如需修改 UI：

1. 找到原始 React + Vite 源码项目，执行 `vite build`
2. 将新产物中的 `assets/` 目录覆盖本仓库 `assets/`
3. ⚠️ 构建后文件名含内容哈希（如 `index-AbCd1234.js`），**必须同步更新 `index.html` 中的 `<script src>` 和 `<link href>` 引用**
4. `rsync` 同步到服务器 + `git push`

### 场景三：在宿主导航页添加新子域名卡片

```bash
# 直接编辑 landing index.html，bind mount 即时生效，无需 reload
ssh -i ai_video.pem ubuntu@101.34.52.232 \
  "nano /opt/ai-video/deploy/lighthouse/landing/index.html"
```

卡片结构参考（复制现有卡片，修改 accent 色类名和内容）：

```html
<a class="card <accent>" href="https://<subdomain>.lute-tlz-dddd.top">
  <div class="card-icon <accent>"><!-- SVG 图标 --></div>
  <p class="card-subtitle <accent>">English Subtitle</p>
  <h2 class="card-title">中文标题</h2>
  <p class="card-desc">中文描述</p>
  <p class="card-desc-en">English description</p>
  <div class="card-meta">
    <span class="chip">标签1</span>
    <span class="chip">标签2</span>
  </div>
  <span class="card-cta <accent>">CTA 文字 →</span>
</a>
```

已用 accent 色：`fortune-red`、`jade`（voc）、`report`（gold）、`shopify`（紫）、`mkt`（暗红）、`business`（莫兰迪棕）、`kg`（蓝）、`person`（teal #3B8C82）。新卡片需选不同颜色。

### 场景四：新增子域名完整流程

1. DNS：腾讯云 DNSPod 添加 A 记录 `<new>.lute-tlz-dddd.top → 101.34.52.232`
2. 静态文件：`mkdir /opt/<new>/html && rsync 文件`
3. nginx：备份 → 追加 server 块 → 验证语法 → reload
4. docker-compose：追加 volume mount → `force-recreate nginx`
5. SSL：`certbot certonly --expand -d ... -d <new>.lute-tlz-dddd.top`
6. 宿主导航页：添加新卡片

### 场景五：迁移到新服务器

1. `rsync /opt/ai-employ-platform/` 到新服务器
2. 新服务器 nginx 配置追加 `person.*` server 块（参考现有 nginx.conf）
3. 扩展 SSL 证书
4. 更新 DNS A 记录

---

## 变更日志

| 日期 | 内容 |
|---|---|
| 2026-05-27 | 项目初始化，推送至 GitHub（`zjgulai/ai-digital-person`），开启 GitHub Pages |
| 2026-05-28 | 修复 HTML `lang` 属性（en→zh-CN），添加 SEO meta；去除 `data/roles.json` 中 40 处重复 model |
| 2026-05-28 | 腾讯云生产部署：SSL 证书 expand、nginx 追加 server 块、docker-compose 追加 volume mount |
| 2026-05-28 | 宿主导航页 [lute-tlz-dddd.top](https://lute-tlz-dddd.top) 添加本项目卡片（第 8 张，Teal 色系）|
| 2026-05-28 | **源码重建**：从 bundle 反推还原完整 React 19 + TypeScript 源码项目（`ai_employ_platform_src`），实现 5 页完整 SPA（首页/市场/详情/定价/关于），含 Tailwind CSS 完整编译 |
| 2026-05-28 | 修复 Tailwind 未编译 bug：PostCSS 配置缺失导致样式全部失效，改用 `postcss.config.mjs` 修复 |

---

## 许可

Copyright © 2026 路特团队. All rights reserved.
