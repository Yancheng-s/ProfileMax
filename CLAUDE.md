# ProfileMax

GitHub 个人主页 README 美化技能 — 多模板、可插拔组件、一键生成。

## 项目结构

```
ProfileMax/
├── SKILL.md                           # 主 skill 入口（Claude Code 加载）
├── README.md                          # 项目首页
├── CLAUDE.md                          # 本文件
├── templates/                         # 6 种风格模板
│   ├── minimal.md                     # 极简·白
│   ├── neon.md                        # 霓虹·暗
│   ├── dashboard.md                   # 仪表盘
│   ├── gamified.md                    # 游戏化
│   ├── creative.md                    # 创意·卡片
│   └── professional.md                # 专业·商务
├── components/                        # 组件 + 工具百科（80+ 工具/服务）
│   ├── complete-reference.md          # 工具百科索引（13 分类，80+ 工具）
│   ├── stats.md                       # 统计卡片工具（10 种服务）
│   ├── badges.md                      # 徽章/图标/访客计数（16 种服务）
│   ├── animations.md                  # 动效/趣味（10 种服务）
│   ├── content-sections.md            # 内容区块（11 种服务）
│   ├── actions.md                     # GitHub Actions（7 种 Action）
│   └── extra-widgets.md               # 音乐/媒体/综合卡片（10+ 种）
├── examples/
│   └── complete-example.md            # 完整示例页面
└── .github/workflows/
    └── snake.yml                      # 贪吃蛇工作流
```

## 设计原则

1. **对话式交互** — Claude Code 收集信息，不是让用户自己改占位符
2. **模板 + 组件** — 6 种风格 × 可插拔组件，灵活组合
3. **端到端自动化** — 如果用户同意，gh CLI 直接创建同名仓库并推送
4. **渐进式复杂度** — 默认推荐精选组件，高级选项折叠展示

## 维护注意

- 添加新模板 → 在 `templates/` 下创建，并更新 `SKILL.md` 的模板表格
- 添加新组件 → 在 `components/` 下创建，并更新 `SKILL.md` 的组件表格
- `SKILL.md` 是 Claude Code 加载的唯一入口，其他文件通过它引用
