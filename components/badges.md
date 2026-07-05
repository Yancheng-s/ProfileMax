<!--
  组件：徽章 / 图标 / 访客计数
  分类：徽章图标 / 技术栈图标 / 访客计数器
-->

## 可用工具总览

| 工具 | 用途 | 推荐度 |
|------|------|--------|
| [skill-icons](https://skillicons.dev) | 100+ 技能图标（亮/暗主题） | ⭐ 首推 |
| [shields.io](https://shields.io) | 通用徽章（标准） | ⭐ 首推 |
| [simple-icons](https://simpleicons.org) | 3200+ 品牌图标库 | 配合 shields |
| [for-the-badge](https://forthebadge.com) | 大号风格徽章 | ⭐ 推荐 |
| [badgen.net](https://badgen.net) | 快速徽章生成 | 可选 |
| [markdown-badges](https://github.com/Ileriayo/markdown-badges) | 精选徽章合集（可直接复制） | ⭐ 推荐 |
| [m3-markdown-badges](https://github.com/Aveek-Saha/M3-Markdown-Badges) | Material You 风格徽章 | 可选 |
| [custom-icon-badges](https://github.com/DenverCoder1/custom-icon-badges) | 自定义图标徽章 | 可选 |
| [gradient-badge](https://github.com/bokub/gradient-badge) | 渐变色徽章 | 可选 |
| [devicon](https://devicon.dev) | 编程语言图标 | 可选 |
| [tech-stack-icons](https://github.com/marwin1991/profile-technology-icons) | 2000+ 技术栈图标 | 可选 |
| [Badges4-README.md-Profile](https://github.com/alexandresanlim/Badges4-README.md-Profile) | 头像/社交/技术徽章合集 | 可选 |
| [komarev/ghpvc](https://komarev.com) | 访客计数 | ⭐ 首推 |
| [hits](https://hits.seeyoufarm.com) | 点击计数 | 可选 |
| [visitor-badge](https://visitor-badge.laobi.icu) | 简洁访客徽章 | 可选 |
| [moe-counter](https://github.com/journey-ad/Moe-Counter) | 萌系访客计数 | 趣味 |

## 技术栈图标 (skill-icons)

使用 https://skillicons.dev 生成统一风格的技术栈图标。

```markdown
![My Skills](https://skillicons.dev/icons?i=ts,react,nextjs,nodejs,python,go,docker,kubernetes,git,figma&perline=8)
```

参数：

| 参数 | 说明 | 示例 |
|------|------|------|
| `icons` | 逗号分隔的图标名 | `ts,react,nextjs` |
| `perline` | 每行显示数量 | `8` |
| `theme` | 亮暗模式 | `light` / `dark` |

常用图标名速查表：

| 技术 | slug | 技术 | slug |
|------|------|------|------|
| TypeScript | `ts` | React | `react` |
| Vue | `vue` | Next.js | `nextjs` |
| Node.js | `nodejs` | Python | `python` |
| Go | `go` | Rust | `rust` |
| Docker | `docker` | Kubernetes | `kubernetes` |
| Git | `git` | GitHub | `github` |
| VS Code | `vscode` | Figma | `figma` |
| Tailwind | `tailwind` | MySQL | `mysql` |
| PostgreSQL | `postgres` | MongoDB | `mongodb` |
| Redis | `redis` | Nginx | `nginx` |
| Linux | `linux` | AWS | `aws` |
| Firebase | `firebase` | GraphQL | `graphql` |

完整列表：https://github.com/tandpfun/skill-icons

---

## Shields.io 徽章

使用 https://shields.io 生成静态徽章。

基础格式：
```markdown
![Static Badge](https://img.shields.io/badge/标签-内容-颜色?style=flat&logo=图标名&logoColor=white)
```

示例：
```markdown
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)
```

常用参数：

| 参数 | 说明 | 值 |
|------|------|----|
| `style` | 风格 | `flat` / `flat-square` / `for-the-badge` / `plastic` / `social` |
| `logo` | 图标名 | Shields.io 支持的图标 slug |
| `logoColor` | 图标颜色 | `white` 或 hex |
| `labelColor` | 标签背景色 | hex 颜色 |
| `color` | 值背景色 | hex 颜色 |

颜色快速参考：

| 颜色名 | Hex | 适合技术 |
|--------|-----|----------|
| 蓝色 | `007ACC` | TypeScript, Python |
| 青色 | `61DAFB` | React, Next.js |
| 绿色 | `43853D` | Node.js, Go |
| 黄绿 | `4FC08D` | Vue |
| 粉色 | `E91E63` | Svelte, Ruby |
| 橙色 | `F05032` | Git, HTML |
| 紫色 | `9146FF` | GraphQL |
| 白色 | `FFFFFF` | 通用 |

---

## 访客计数器

### 方案一：Komarev（推荐）

```markdown
![Visitor Count](https://komarev.com/ghpvc/?username={{USERNAME}}&color=brightgreen&style=flat-square&label=访客)
```

参数：

| 参数 | 说明 |
|------|------|
| `color` | 颜色（brightgreen / green / yellow / red / blue / lightgrey / 自定义 hex） |
| `style` | 风格（flat / flat-square / for-the-badge） |
| `label` | 自定义标签文字 |
| `base` | 起始计数（默认 0） |

### 方案二：Profile Views Counter

```markdown
![Profile Views](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https://github.com/{{USERNAME}}&count_bg=%2379C83D&title_bg=%23555555&icon=github.svg&icon_color=%23E7E7E7&title=访客&edge_flat=true)
```

### 方案三：直接在 README 中不显示原始数字

```markdown
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://komarev.com/ghpvc/?username={{USERNAME}}&style=flat-square&label=Visitors&color=blue">
  <source media="(prefers-color-scheme: light)" srcset="https://komarev.com/ghpvc/?username={{USERNAME}}&style=flat-square&label=Visitors&color=blue">
  <img src="https://komarev.com/ghpvc/?username={{USERNAME}}&style=flat-square&label=Visitors&color=blue">
</picture>
```
