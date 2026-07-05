<!--
  组件：额外小部件
  服务：readme-jokes, github-readme-quotes, github-profile-3d-contrib, profile-summary-for-github, github-profile-summary-cards
-->

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

```markdown
![Quote](https://github-readme-quotes.herokuapp.com/quote)
```

主题色：
```markdown
![Quote](https://github-readme-quotes.herokuapp.com/quote?theme=dracula&animation=grow_out_in)
```

参数：

| 参数 | 说明 |
|------|------|
| `theme` | 主题：dark, radical, dracula, tokyonight 等 |
| `animation` | 动画：grow_out_in, fade_in, fade_out 等 |
| `layout` | 布局：default, modern |

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

## GitHub 个人总结页 (profile-summary-for-github)

```markdown
![](https://raw.githubusercontent.com/{{USERNAME}}/{{USERNAME}}/main/profile-summary-card-output/README.md)
```

或者直接嵌入网页版链接：

```markdown
[https://profile-summary-for-github.netlify.app/](https://profile-summary-for-github.netlify.app/)
```
