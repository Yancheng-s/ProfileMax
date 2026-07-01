# ProfileMax

GitHub 个人主页 README 美化 — Claude Code skill

## 安装

```bash
git clone https://github.com/<你的用户名>/ProfileMax.git
mkdir -p .claude/skills/profilemax
cp -r ProfileMax/* .claude/skills/profilemax/
```

或者用 skills.sh：

```bash
npx skills add <你的用户名>/ProfileMax
```

## 使用

在 Claude Code 中输入：

```
帮我美化 GitHub 主页
```

或：

```
/profilemax
```

Claude 会依次问你：用户名、介绍、技术栈、风格偏好、额外组件。回答完即生成完整 README。

## 文件结构

```
ProfileMax/
├── SKILL.md                           ← 技能入口（核心）
├── templates/                         ← 6 种风格模板
│   ├── minimal.md       极简·白
│   ├── neon.md          霓虹·暗
│   ├── dashboard.md     仪表盘
│   ├── gamified.md      游戏化
│   ├── creative.md      创意·卡片
│   └── professional.md  专业·商务
├── components/                        ← 可插拔组件参考
│   ├── stats.md
│   ├── badges.md
│   ├── animations.md
│   ├── content-sections.md
│   └── actions.md
├── examples/
│   └── complete-example.md
└── .github/workflows/
    └── snake.yml
```

## LICENSE

MIT
