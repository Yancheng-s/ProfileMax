<!--
  组件：额外小部件
  分类：编程笑话 / 每日名言 / 音乐媒体 / 趣味 / 综合
-->

## 可用工具总览

| 工具 | 用途 | 推荐度 |
|------|------|--------|
| [readme-jokes](https://github.com/ajyan/readme-jokes) | 编程笑话（可自建 Vercel 实例） | ⭐ 推荐 |
| [github-readme-quotes](https://github.com/cheehwatang/github-readme-daily-quotes) | 开发名言（可自建 Vercel 实例） | ⭐ 推荐 |
| [random-meme](https://github.com/techytushar/random-meme) | 随机编程梗图 | 趣味 |
| [Codeforces Readme Stats](https://codeforces-readme-stats.vercel.app/api/card?username=) | 算法竞赛 Codeforces 数据卡 | ⭐ 竞赛玩家 |
| [GitHub Streak Widget](https://github-streak-widget.vercel.app) | Duolingo 风格连胜徽章 | ⭐ 趣味 |
| [GitWrap](https://gitwrap.vercel.app) | 年度编码回顾卡片（免登录） | ⭐ 年度回顾 |
| [octocanvas](https://github.com/github/octocanvas) | GitHub 官方收藏卡片 | 官方 |
| [spotify-github-profile](https://github.com/kittinan/spotify-github-profile) | 正在播放 Spotify | 需登录 |
| [novatorem](https://github.com/novatorem/novatorem) | Spotify 替代方案 | 需登录 |
| [chess-com-stats](https://github.com/Balastrong/chess-com-stats) | 国际象棋统计 | 可选 |
| [goodreads-readme](https://github.com/Yizack/goodreads-readme) | 正在读的书 | 可选 |
| [youtube-stats](https://github.com/DenverCoder1/github-readme-youtube-stats) | YouTube 订阅数 | 可选 |
| [lowlighter/metrics](https://github.com/lowlighter/metrics) | 40+ 插件信息图生成器 | ⭐ 推荐 |
| [coolreadme.xyz](https://coolreadme.xyz) | 34+ 卡片（宠物/Netflix/Steam/YC/HN等） | ⭐ 推荐（见下方） |
| [DevDNA](https://devdna.netlify.app) | 开发者性格分析卡片（需自建实例绕过 API 限流） | ⭐ 2026 新品 |
| [galaxy-profile](https://github.com/vinimlo/galaxy-profile) | 星系风格个人主页（需 Action） | ⭐ 趣味 |
| [statsvg-rs](https://github.com/akshay2211/statsvg_rs) | Rust 渲染 SVG 统计（Action 生成，零服务器） | ⭐ 创新方案 |

> 注：以上公共实例偶有过载，如需稳定使用可 fork 对应仓库并自建 Vercel 实例。

## 自建指南

如果公共实例不可用，可以 fork 项目到自己账号，一键部署到免费 Vercel：

| 项目 | 一键部署 |
|------|---------|
| readme-jokes | Fork → Vercel 导入 → 自动部署 |
| github-readme-daily-quotes | Fork → Vercel 导入 → 自动部署 |
| github-profile-summary-cards | Fork → Vercel 导入 → 自动部署 |
| github-readme-stats | Fork → 创建 PAT → Vercel 导入 → 设置 `PAT_1` 环境变量 → 部署 |

## coolreadme.xyz 卡片（2026 新兴平台）

34+ 种免费卡片，无需注册。部分热门类型：

| 卡片 | 说明 |
|------|------|
| 宠物连胜卡 🦊🐧🦉🐱🐶 | 9 阶段进化，根据提交连胜天数自动进化 |
| Y Combinator 卡片 | 公司名称/批次/状态（launching/hiring/stealth） |
| Hacker News 卡片 | Show HN / Ask HN / Launch HN |
| Linear 卡片 | 任务进度 Backlog → In Progress → Done |
| Letterboxd 卡片 | 电影评分（5星制） |
| Duolingo 卡片 | 语言学习连胜（含猫头鹰表情） |
| Netflix 卡片 | 影视卡片风格 |
| Steam 卡片 | 游戏平台风格 |
| AI Identity 卡片 | AI 开发者身份标识 |
| Spotify 正在播放 | 音乐卡片风格 |

## 编程笑话 (readme-jokes)

```markdown
![Jokes](https://readme-jokes.vercel.app/api)
```

暗色主题：
```markdown
![Jokes](https://readme-jokes.vercel.app/api?theme=dracula)
```

---

## 每日名言 (github-readme-quotes)

> 注意：Heroku 版已下线，使用 PiyushSuthar 的 Vercel 版本。

```markdown
![Quote](https://quotes-github-readme.vercel.app/api?type=horizontal&theme=dark)
```

主题色：
```markdown
![Quote](https://quotes-github-readme.vercel.app/api?type=horizontal&theme=dracula)
```

参数：

| 参数 | 说明 |
|------|------|
| `type` | 布局：`horizontal`, `vertical` |
| `theme` | 主题：dark, radical, dracula, tokyonight 等 |

---

## 3D 贡献图

使用 https://github.com/yoshi389111/github-profile-3d-contrib 生成 3D 贡献日历。

需要配置 GitHub Action：

```yaml
name: GitHub-Profile-3D-Contrib

on:
  schedule:
    - cron: "0 18 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    name: generate-github-profile-3d-contrib
    steps:
      - uses: actions/checkout@v4
      - uses: yoshi389111/github-profile-3d-contrib@main
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          USERNAME: ${{ github.repository_owner }}
      - name: Commit & Push
        run: |
          git add -A
          git diff --staged --quiet || git commit -m "chore: update 3d contrib"
          git push
```

然后在 README 中引用：

```markdown
<img src="https://raw.githubusercontent.com/{{USERNAME}}/{{USERNAME}}/main/profile-3d-contrib/profile-night-rainbow.svg" />
```

---

## Codeforces 竞赛数据卡 (Codeforces Readme Stats)

适用于参与算法竞赛的开发者：

```markdown
![Codeforces Stats](https://codeforces-readme-stats.vercel.app/api/card?username=YourCodeforcesHandle)
```

主题色：
```markdown
![Codeforces](https://codeforces-readme-stats.vercel.app/api/card?username=YourHandle&theme=dark&disable_animations=true)
```

---

## Octocanvas (GitHub 官方收藏卡)

GitHub 官方项目，生成个人风格收藏卡片：

```markdown
![Octocard](https://octocanvas.vercel.app/api/card?username={{USERNAME}})
```

---

## GitWrap 年度回顾卡

生成年度编码回顾卡片，无需登录：

```markdown
![GitWrap](https://gitwrap.vercel.app/api/card?username={{USERNAME}})
```

---

## GitHub 个人总结页 (profile-summary-for-github)

```markdown
![](https://raw.githubusercontent.com/{{USERNAME}}/{{USERNAME}}/main/profile-summary-card-output/README.md)
```

或者直接嵌入网页版链接：

```markdown
[https://profile-summary-for-github.netlify.app/](https://profile-summary-for-github.netlify.app/)
```
