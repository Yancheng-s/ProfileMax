---
name: profilemax
description: "GitHub Profile README 美化 — 6 种模板、可插拔组件、对话式生成"
---

# ProfileMax

## 触发

用户说以下任一时，调用此 skill：
- 美化 GitHub 主页
- 帮我做一个好看的 GitHub Profile
- `/profilemax`
- 生成个人主页 README

## 工作流

### 第一步：收集信息（一个一个问，别全抛）

**① GitHub 用户名**
```
你的 GitHub 用户名是什么？
```

**② 一句话介绍**
```
你怎么介绍自己？比如"全栈开发者"、"开源爱好者"、"前端工程师"。
```

**③ 技术栈**
```
你主要用什么技术？
按熟练度列出就行，比如：React, TypeScript, Node.js, Python, Docker
```

**④ 风格**
```
以下是 6 种风格，你想要哪种？

1. 极简 — 干净留白、左对齐，适合设计师/前端
2. 霓虹 — 深色+霓虹渐变，动感炫酷
3. 仪表盘 — 数据密集，卡片并排展示
4. 游戏化 — 奖杯+Level+贪吃蛇，适合年轻开发者
5. 创意 — 头像卡片+波浪头图
6. 专业 — Shields 徽章排布，克制、求职向
```

**⑤ 额外展示内容（多选）**
```
还想加什么？（可以多选，都不要就回车跳过）
a. 最新博客文章 (需要提供 RSS 链接)
b. 精选项目展示 (自动读取你的置顶仓库)
c. 社交链接 (Twitter/B站/知乎/掘金等)
d. 关于我段落
e. 访客计数器
f. 贪吃蛇动画 (需要配置 GitHub Action)
g. 都不要
```

### 第二步：拼接 README

根据用户选择，从 `templates/` 加载对应的模板文件，从 `components/` 加载对应的组件代码。

占位符映射：

| 占位符 | 来源 | 说明 |
|--------|------|------|
| `{{USERNAME}}` | 用户输入 | GitHub 用户名 |
| `{{BIO}}` | 用户输入 | 一句话介绍 |
| `{{ABOUT_ME}}` | 用户输入的关于我 | 可省略 |
| `{{TECH_STACK_ICONS}}` | skill-icons | 根据技术栈生成 |
| `{{TECH_STACK_BADGES}}` | shields.io | 根据技术栈生成 |
| `{{GITHUB_STATS}}` | github-readme-stats | Stats 卡片 IMG 标签 |
| `{{TOP_LANGS}}` | github-readme-stats | 语言分布 IMG 标签 |
| `{{STREAK}}` | github-readme-streak-stats | Streak 卡片 IMG 标签 |
| `{{TROPHY}}` | github-profile-trophy (镜像) | 奖杯 IMG 标签 |
| `{{ACTIVITY_GRAPH}}` | github-readme-activity-graph | 折线图 IMG 标签 |
| `{{TYPING_SVG}}` | readme-typing-svg | 打字动画 IMG 标签 |
| `{{SOCIAL_LINKS}}` | 用户提供的社交账号 | shield.io 徽章行 |
| `{{BLOG_POSTS}}` | 用户提供的 RSS | 手动列表或 Action 占位 |
| `{{VISITOR_COUNTER}}` | komarev | 访客计数 IMG |
| `{{SHOWCASE}}` | 用户指定的仓库 | github-readme-stats pin 卡片 |
| `{{SNAKE}}` | Platane/snk | 贪吃蛇 IMG |

### 第三步：生成 README

把拼接好的完整 README.md 展示给用户。按以下格式：

````markdown
以下是你的 GitHub 主页 README：

```markdown
[完整的 README 代码]
```

使用步骤：
1. 创建一个和你 GitHub 用户名同名的仓库（如果还没有的话）
2. 把上面的代码粘贴到 README.md
3. 推送到 GitHub，主页就生效了
````

如果用户选了贪吃蛇，额外提供 `.github/workflows/snake.yml` 文件内容。

### 第四步：自动部署

用户说"部署"、"推送"、"上传"、"cli"、"帮我建仓库" 或流露出想直接上线的意愿时，直接进入自动部署流程。不需要再问"要不要"——用户说了就是想要。

#### 4.1 检查 gh CLI

```bash
gh --version 2>/dev/null || echo "not installed"
```

如果没装，根据不同平台提示安装命令：

- **Windows**: `winget install --id GitHub.cli` 或去 https://cli.github.com/ 下载
- **macOS**: `brew install gh`
- **Linux**: `sudo apt install gh` / `sudo dnf install gh`

装完后继续下一步。

#### 4.2 登录（如需要）

```bash
gh auth status 2>/dev/null || gh auth login --web
```

`gh auth login --web` 会打印一个 8 位验证码并自动打开浏览器。让用户确认授权即可。

如果用户说"已经在浏览器确认了"但状态还是未登录，可能是浏览器没打开，直接让用户复制验证码去 https://github.com/login/device 手动输入。

#### 4.3 检查同名仓库

```bash
gh repo view <USERNAME>/<USERNAME> --json name 2>/dev/null && echo "exists" || echo "not exists"
```

- `not exists` → 直接创建
- `exists` → 问用户："同名仓库已存在，是覆盖 README 还是跳过？" 覆盖就继续，跳过就结束

#### 4.4 创建并推送

```bash
# 创建仓库（如果不存在）
gh repo create <USERNAME>/<USERNAME> --public \
  --description "My GitHub Profile README"

# 临时目录初始化
cd /tmp
rm -rf profilemax-deploy
mkdir profilemax-deploy
cd profilemax-deploy

git init
git config user.name "<USERNAME>"
git config user.email "<USERNAME>@users.noreply.github.com"

# 写入 README.md
cat > README.md << 'EOF'
[生成的 README 完整内容]
EOF

# 如果选了贪吃蛇，写入 .github/workflows/snake.yml
mkdir -p .github/workflows
cat > .github/workflows/snake.yml << 'EOF'
[snake.yml 内容]
EOF

git add -A
git commit -m "feat: init profile README"
git branch -M main
git remote add origin https://github.com/<USERNAME>/<USERNAME>.git
git push -u origin main

# 清理
cd /
rm -rf profilemax-deploy
```

#### 4.5 完成

打印部署结果，建议用户去确认效果：

```
部署成功！
主页地址：https://github.com/<USERNAME>

贪吃蛇动画可能需要先手动运行一次 GitHub Action 才会显示。
路径：仓库 -> Actions -> Generate Snake -> Run workflow
```

## 模板索引

| 模板 | 文件 | 调性 | 布局 |
|------|------|------|------|
| 极简·白 | templates/minimal.md | 干净、留白 | 左对齐 |
| 霓虹·暗 | templates/neon.md | 深色+渐变、动感 | 居中 |
| 仪表盘 | templates/dashboard.md | 数据密集、卡片并排 | 表格居中 |
| 游戏化 | templates/gamified.md | 奖杯、等级、成就 | 居中 |
| 创意·卡片 | templates/creative.md | 头像+波浪头、视觉个性 | 居中+表格 |
| 专业·商务 | templates/professional.md | 克制、徽章排布 | 左对齐 |

## 组件索引

| 组件 | 文件 |
|------|------|
| GitHub Stats / Top Langs / Streak | components/stats.md |
| Trophy / Activity Graph | components/stats.md |
| 技术栈图标 (skill-icons) | components/badges.md |
| Shields.io 自定义徽章 | components/badges.md |
| 访客计数器 | components/badges.md |
| Typing SVG 打字动画 | components/animations.md |
| 贪吃蛇 | components/animations.md |
| 波浪头图 (capsule-render) | components/animations.md |
| 关于我 / 博客 / 项目展示 / 社交链接 | components/content-sections.md |
| GitHub Actions 自动更新 | components/actions.md |

## 重要规则

1. 生成 README 时，所有 `{{USERNAME}}` 必须替换为实际的用户名，不要留占位符让用户自己改
2. 如果用户没给技术栈，不要瞎编 — 问清楚再继续
3. skill-icons 优先于 shields.io 展示技术栈（更好看、更统一）
4. 所有 shields.io 徽章的 logo 参数用官方 slug（小写），不要自定义
5. 统计卡片统一加 `&hide_border=true` 让边缘更干净
6. 默认主题用 `radical`，除非用户指定了别的
7. 用户选贪吃蛇时，必须同时生成 `.github/workflows/snake.yml`，否则图挂掉
8. 生成的 README 本身不要包含 `<!--` 注释内容 — 那是给 skill 开发者看的，不是给最终用户的
9. 布局：极简和专业模板左对齐，其他居中
10. 统计卡片 URL 中的 `username` 注意大小写敏感，和 GitHub 用户名完全一致
