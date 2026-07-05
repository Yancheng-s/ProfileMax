<!--
  组件：内容区块
  分类：关于我 / 博客文章 / 项目展示 / 社交链接
-->

## 可用工具总览

| 工具 | 用途 | 推荐度 |
|------|------|--------|
| [blog-post-workflow (Action)](https://github.com/gautamkrishnar/blog-post-workflow) | 自动更新博客文章（RSS/知乎/掘金等） | ⭐ 首推 |
| [github-activity-readme (Action)](https://github.com/jamesgeorge007/github-activity-readme) | 最近 GitHub 活动 | ⭐ 推荐 |
| [gh-stats.com pin](https://gh-stats.com) | 项目展示卡片 | ⭐ 首推 |
| [socialify](https://socialify.git.ci) | 社交风格项目图片 | 可选 |
| [star-history](https://star-history.com) | Stars 增长图 | 可选 |
| [github-readme-linkedin](https://github.com/JithenKS/github-readme-linkedin) | LinkedIn 资料卡 | 可选 |
| [github-readme-stackoverflow](https://github.com/omidnikrah/github-readme-stackoverflow) | StackOverflow 积分 | 可选 |
| [github-readme-twitter](https://github.com/gazf/github-readme-twitter) | 最新推文 | 可选 |
| [waka-readme-stats (Action)](https://github.com/anmol098/waka-readme-stats) | WakaTime 编码统计 | ⭐ 推荐 |
| [lanyard-profile-readme](https://github.com/Phineas/lanyard-profile-readme) | Discord 在线状态 | 可选 |
| [todoist-readme](https://github.com/abhisheknaiidu/todoist-readme) | Todoist 任务统计 | 可选 |

## 关于我

推荐写法（简明扼要）：

```markdown
## 关于我

- 目前正在做：{{current_project}}
- 正在学习：{{learning}}
- 寻求合作：{{collab}}
- 问我关于：{{expertise}}
- 联系我：{{contact}}
- 有趣的事：{{fun_fact}}
```

或者段落形式：

```markdown
<p align="left">
  {{BIO_PARAGRAPH}}
</p>
```

---

## 博客最新文章

### 方案一：手动维护

```markdown
## 最新博文

- [文章标题 1](https://blog.example.com/post1)
- [文章标题 2](https://blog.example.com/post2)
- [文章标题 3](https://blog.example.com/post3)
```

### 方案二：GitHub Action 自动更新（推荐）

使用 https://github.com/gautamkrishnar/blog-post-workflow

在 `.github/workflows/blog-post-workflow.yml`：

```yaml
name: Latest blog post workflow
on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

jobs:
  update-readme:
    name: Update README with latest blog posts
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: gautamkrishnar/blog-post-workflow@v1
        with:
          feed_list: "https://example.com/feed.xml"
          max_post_count: 5
          readme_path: ./README.md
          template: "- [$title]($url) — $date"
          comment_tag_name: BLOG-POSTS
```

然后在 README 中标记位置：

```markdown
## 最新博文

<!-- BLOG-POSTS:START -->
<!-- BLOG-POSTS:END -->
```

支持的数据源：RSS / Atom / 知乎 / 掘金 / 简书 / Medium / Dev.to / Hashnode

---

## 项目展示（Showcase）

```markdown
## 精选项目

<div align="center">

[![Readme Card](https://gh-stats.com/api/pin?username={{USERNAME}}&repo=repo1)](https://github.com/{{USERNAME}}/repo1)
[![Readme Card](https://gh-stats.com/api/pin?username={{USERNAME}}&repo=repo2)](https://github.com/{{USERNAME}}/repo2)

</div>
```

参数：

| 参数 | 说明 |
|------|------|
| `username` | 所有者 |
| `repo` | 仓库名 |
| `theme` | 主题色 |
| `show_owner` | 显示所有者（用于 fork 的仓库） |
| `hide_border` | 隐藏边框 |

---

## 社交链接

```markdown
## 社交链接

<div align="center">

[![Twitter](https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/{{handle}})
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/{{handle}})
[![Bilibili](https://img.shields.io/badge/Bilibili-FB7299?style=for-the-badge&logo=bilibili&logoColor=white)](https://space.bilibili.com/{{uid}})
[![Zhihu](https://img.shields.io/badge/知乎-0066FF?style=for-the-badge&logo=zhihu&logoColor=white)](https://www.zhihu.com/people/{{handle}})
[![Juejin](https://img.shields.io/badge/掘金-1E80FF?style=for-the-badge&logo=bytedance&logoColor=white)](https://juejin.cn/user/{{uid}})
[![Website](https://img.shields.io/badge/网站-000000?style=for-the-badge&logo=about.me&logoColor=white)](https://{{website}})

</div>
```

常用平台速查：

| 平台 | 徽章颜色 | Logo Slug | URL 格式 |
|------|----------|-----------|----------|
| Twitter/X | `1DA1F2` | `twitter` | `https://twitter.com/{{username}}` |
| LinkedIn | `0077B5` | `linkedin` | `https://linkedin.com/in/{{username}}` |
| Bilibili | `FB7299` | `bilibili` | `https://space.bilibili.com/{{uid}}` |
| 知乎 | `0066FF` | `zhihu` | `https://www.zhihu.com/people/{{handle}}` |
| 掘金 | `1E80FF` | `juejin` | `https://juejin.cn/user/{{uid}}` |
| 微博 | `E6162D` | `sina-weibo` | `https://weibo.com/{{handle}}` |
| 小红书 | `FF2442` | `xiaohongshu` | `https://www.xiaohongshu.com/user/{{uid}}` |
| CSDN | `FC5531` | CSDN 无官方 logo | `https://blog.csdn.net/{{handle}}` |
| Email | `D14836` | `gmail` | `mailto:{{email}}` |
| 个人网站 | `000000` | `about.me` | `https://{{domain}}` |
| Stack Overflow | `F58025` | `stackoverflow` | `https://stackoverflow.com/users/{{uid}}` |
| Dev.to | `0A0A0A` | `dev.to` | `https://dev.to/{{username}}` |

---

## 访客计数器

见 [badges.md](badges.md) 中的访客计数器部分。
