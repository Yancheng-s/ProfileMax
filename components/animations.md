<!--
  组件：动效
  分类：打字动画 / 贪吃蛇 / 波浪头图 / 3D 贡献图
-->

## 可用工具总览

| 工具 | 用途 | 推荐度 |
|------|------|--------|
| [readme-typing-svg](https://readme-typing-svg.demolab.com) | 打字动画 | ⭐ 首推 |
| [snk (贪吃蛇)](https://github.com/Platane/snk) | 贡献图变贪吃蛇（需 Action） | ⭐ 首推 |
| [capsule-render](https://github.com/kyechan99/capsule-render) | 波浪头图/页脚 | ⭐ 首推 |
| [github-profile-3d-contrib](https://github.com/yoshi389111/github-profile-3d-contrib) | 3D 贡献日历（需 Action） | ⭐ 推荐 |
| [skyline (官方)](https://skyline.github.com) | 3D 城市天际线 | 官方 |
| [github-spray](https://github.com/Annihil/github-spray) | 在贡献图画图 | 趣味 |
| [REHeader](https://github.com/khalby786/REHeader) | 页眉图片生成器 | 可选 |
| [svg-banners](https://github.com/Akshay090/svg-banners) | SVG 横幅 | 可选 |
| [readme-jokes](https://readme-jokes.vercel.app/api) | 编程笑话 | ⭐ 推荐 |
| [github-readme-quotes](https://github-readme-quotes.herokuapp.com/quote) | 开发名言 | ⭐ 推荐 |
| [random-meme](https://github.com/techytushar/random-meme) | 随机编程梗图 | 趣味 |

## Typing SVG 打字动画

使用 https://readme-typing-svg.demolab.com 生成打字机效果。

```markdown
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&duration=3000&pause=1000&color=A78BFA&center=true&vCenter=true&width=500&lines=Full+Stack+Developer;Open+Source+Enthusiast;UI%2FUX+Lover&repeat=true" />
```

参数：

| 参数 | 说明 | 推荐值 |
|------|------|--------|
| `font` | 字体 | `Fira+Code` / `JetBrains+Mono` / `Press+Start+2P` |
| `size` | 字号 | `22` ~ `30` |
| `duration` | 单行停留 ms | `3000` ~ `5000` |
| `pause` | 切换停顿 ms | `500` ~ `1500` |
| `color` | 字体色 hex | `A78BFA` (紫) / `7AA2F7` (蓝) |
| `center` | 居中 | `true` |
| `vCenter` | 垂直居中 | `true` |
| `width` | 容器宽度 | `400` ~ `600` |
| `height` | 容器高度 | 可选 |
| `lines` | 多行文字，用 `;` 分隔 | `line1;line2;line3` |
| `repeat` | 循环 | `true` |
| `random` | 随机播放 | `false` |

多行写法：
```
lines=Hello!;I'm+a+Dev;I+love+Claude
```

---

## 贪吃蛇动画（Snake Game）

使用 https://github.com/Platane/snk 生成贪吃蛇吃掉贡献图的动画。

### 需要配置 GitHub Action

在 `.github/workflows/snake.yml` 中配置：

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

然后在 README 中引用：
```markdown
<img src="https://raw.githubusercontent.com/{{USERNAME}}/{{USERNAME}}/output/github-contribution-grid-snake-dark.svg" />
```

### 也可以直接用 GitHub Pages 链接（更可靠）

```markdown
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/{{USERNAME}}/{{USERNAME}}/output/github-contribution-grid-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/{{USERNAME}}/{{USERNAME}}/output/github-contribution-grid-snake.svg" />
  <img src="https://raw.githubusercontent.com/{{USERNAME}}/{{USERNAME}}/output/github-contribution-grid-snake.svg" />
</picture>
```

**注意：** 这需要预先运行一次 Action 生成 SVG 图片，否则链接 404。

---

## 波浪头图（Capsule Render）

使用 https://github.com/kyechan99/capsule-render 生成动态头图。

```markdown
<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=200&section=header&text=Hello!&fontSize=60&animation=twinkling" />
```

参数：

| 参数 | 说明 | 推荐值 |
|------|------|--------|
| `type` | 形状 | `waving` / `rect` / `rounded` / `shark` / `cylinder` / `slice` / `egg` / `venom` / `soft` |
| `color` | 颜色 | `gradient` / `random` / hex 值 |
| `customColorList` | 渐变颜色组合 | `0,2,4,6,12,20` |
| `height` | 高度 | `150` ~ `250` |
| `section` | 部位 | `header` / `footer` |
| `text` | 文字 | URL 编码 |
| `fontSize` | 字号 | `30` ~ `80` |
| `fontAlignY` | 文字垂直位置 | `35` ~ `55` |
| `animation` | 动效 | `twinkling` / `fadeIn` / `fadeOut` |
| `desc` | 副标题 | URL 编码 |

常用组合：

波浪头（推荐）：
```
type=waving&color=gradient&customColorList=6,12,20&height=200&section=header&text=Hi&fontSize=60&animation=twinkling
```

矩形头（更简洁）：
```
type=rect&color=gradient&customColorList=0,2,4&height=150&section=header&text=Hello&fontSize=50
```
