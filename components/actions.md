<!--
  组件：GitHub Actions 自动化
  说明：提供常用的 GitHub Actions 工作流，用于自动更新 README 数据
-->

## 可用 Action 总览

| Action | 用途 | 推荐度 |
|--------|------|--------|
| [Platane/snk](https://github.com/Platane/snk) | 贪吃蛇动画 | ⭐ 首推 |
| [blog-post-workflow](https://github.com/gautamkrishnar/blog-post-workflow) | 博客文章自动更新 | ⭐ 首推 |
| [waka-readme-stats](https://github.com/anmol098/waka-readme-stats) | WakaTime 编码统计 | ⭐ 推荐 |
| [github-activity-readme](https://github.com/jamesgeorge007/github-activity-readme) | 最近 GitHub 活动 | 可选 |
| [yoshi389111/3d-contrib](https://github.com/yoshi389111/github-profile-3d-contrib) | 3D 贡献图 | ⭐ 推荐 |
| [profile_stack](https://github.com/gleich/profile_stack) | 自动生成技术栈表格 | 可选 |
| [rahul-jha98/stats-transparent](https://github.com/rahul-jha98/github-stats-transparent) | 透明背景统计卡 | 进阶 |

## 1. 贪吃蛇动画工作流

文件位置：`.github/workflows/snake.yml`

```yaml
name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

---

## 2. 博客文章自动更新工作流

文件位置：`.github/workflows/blog-update.yml`

```yaml
name: Update Blog Posts

on:
  schedule:
    - cron: "0 6 * * *"
  workflow_dispatch:

jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: gautamkrishnar/blog-post-workflow@v1
        with:
          feed_list: |
            https://example.com/rss
            https://example.com/feed.xml
          max_post_count: 5
          template: "- [$title]($url) — $date"
          retry_count: 3
          retry_max_delay: 600
```

**支持的数据源格式：**
- RSS/Atom Feed
- 知乎专栏
- 掘金
- 简书
- Medium
- Dev.to
- Hashnode

**多种模板格式：**

```yaml
# 仅标题+链接
template: "- [$title]($url)"

# 含日期
template: "- [$title]($url) — $date"

# 含描述
template: "- [$title]($url) — $description"

# 卡片风格
template: "<li><a href='$url'>$title</a> · <code>$date</code></li>"
```

---

## 3. WakaTime 编码统计工作流

文件位置：`.github/workflows/wakatime.yml`

```yaml
name: WakaTime Readme

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - uses: anmol098/waka-readme-stats@master
        with:
          WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}
          GH_TOKEN: ${{ secrets.GH_TOKEN }}
          SHOW_OS: "True"
          SHOW_PROJECTS: "True"
          SHOW_EDITORS: "True"
          SHOW_LANGUAGE: "True"
          SHOW_LANGUAGE_PER_REPO: "True"
          SHOW_TIMEZONE: "True"
          SHOW_COMMIT: "True"
          SHOW_DAYS_OF_WEEK: "True"
```

**前置条件：**
1. 在 https://wakatime.com 注册并获取 API Key
2. 设置 GitHub Secrets: `WAKATIME_API_KEY`, `GH_TOKEN`
3. 在 IDE 中安装 WakaTime 插件

---

## 4. 定时更新所有统计卡片（全面刷新）

文件位置：`.github/workflows/refresh-stats.yml`

```yaml
name: Refresh Stats

on:
  schedule:
    - cron: "0 8 * * *"
  workflow_dispatch:

jobs:
  refresh:
    runs-on: ubuntu-latest
    steps:
      - name: Refresh GitHub Stats (通过请求强制刷新 Vercel 缓存)
        run: |
          curl -s -o /dev/null "https://github-readme-stats.vercel.app/api?username=${{ github.repository_owner }}&show_icons=true&count_private=true"
          curl -s -o /dev/null "https://github-readme-stats.vercel.app/api/top-langs/?username=${{ github.repository_owner }}&layout=compact"
          curl -s -o /dev/null "https://github-readme-streak-stats.herokuapp.com/?user=${{ github.repository_owner }}"
          echo "Stats cache refreshed at $(date)"
```

---

## 5. Workspace 元数据自动更新（VSCode 编码时长等）

文件位置：`.github/workflows/update-meta.yml`

```yaml
name: Update Metadata

on:
  schedule:
    - cron: "0 2 * * *"
  workflow_dispatch:

jobs:
  update:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Update README with current date
        run: |
          echo "Last updated: $(date -u '+%Y-%m-%d %H:%M UTC')" >> README.md.tmp
      - uses: stefanzweifel/git-auto-commit-action@v5
        with:
          commit_message: "chore: update metadata"
```

---

## 重要提醒

1. **GITHUB_TOKEN 权限**：默认的 `secrets.GITHUB_TOKEN` 只有仓库权限，如果需要跨仓库操作，需要创建 Personal Access Token
2. **调度时间**：建议错开整点高峰（不要用 `0 * * * *`），推荐 `23 * * * *` 或 `37 * * * *` 这种偏移时间
3. **workflow_dispatch**：始终加上，方便手动触发
4. **首次运行**：大多数 Action 需要先在 Actions 页面手动运行一次才能看到效果
