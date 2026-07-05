<!--
  组件：统计卡片
  服务：github-readme-stats, github-readme-streak-stats, github-profile-trophy, github-readme-activity-graph
-->

## GitHub Stats 卡片

基础用法：
```markdown
![{{USERNAME}}'s GitHub stats](https://gh-stats.com/api?username={{USERNAME}}&show_icons=true&count_private=true&hide_border=true)
```

常用参数：

| 参数 | 说明 | 推荐值 |
|------|------|--------|
| `show_icons` | 显示图标 | `true` |
| `count_private` | 包含私有仓库 | `true` |
| `include_all_commits` | 包含所有提交 | `true` |
| `hide_border` | 隐藏边框 | `true` |
| `rank_icon` | 等级图标 | `github` 或 `percentile` |
| `bg_color` | 背景色 | 自定义颜色 hex 或 `0D1117` |
| `theme` | 预设主题 | radical / onedark / dracula 等 |
| `hide` | 隐藏某些项目 | `?hide=issues,contribs` |
| `custom_title` | 自定义标题 | `?custom_title=My+Stats` |

---

## Top Languages 卡片

```markdown
![Top Langs](https://gh-stats.com/api/top-langs?username={{USERNAME}}&layout=compact&hide_border=true&langs_count=8)
```

参数：

| 参数 | 说明 | 推荐值 |
|------|------|--------|
| `layout` | 布局 | `compact` / `donut` / `pie` |
| `langs_count` | 语言数量 | `6` ~ `10` |
| `hide` | 隐藏某些语言 | `?hide=html,css` |

---

## Streak 连续提交

```markdown
![GitHub Streak](https://github-readme-streak-stats.herokuapp.com/?user={{USERNAME}}&theme=radical&hide_border=true)
```

参数：

| 参数 | 说明 |
|------|------|
| `theme` | 主题色 |
| `hide_border` | 隐藏边框 |
| `background` | 自定义背景色 |
| `date_format` | 日期格式（`M j[, Y]`） |
| `mode` | `daily` / `weekly` / `monthly` |

---

## Trophy 成就奖杯

```markdown
![trophy](https://github-profile-trophy.vercel.app/?username={{USERNAME}}&theme=radical&no-frame=true&no-bg=true&margin-w=4&row=2&column=4)
```

参数：

| 参数 | 说明 | 推荐值 |
|------|------|--------|
| `theme` | 主题 | radical / onedark / dracula 等 |
| `no-frame` | 无边框 | `true` |
| `no-bg` | 无背景 | `true`（暗色主题） |
| `row` | 行数 | `2` |
| `column` | 列数 | `3~6` |
| `margin-w` | 水平间距 | `4~15` |
| `margin-h` | 垂直间距 | `4~15` |

---

## Activity Graph 活动折线图

```markdown
![Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username={{USERNAME}}&theme=radical&hide_border=true&area=true&custom_title=最近31天活动)
```

参数：

| 参数 | 说明 | 推荐值 |
|------|------|--------|
| `theme` | 主题 | radical / github-dark / etc. |
| `hide_border` | 隐藏边框 | `true` |
| `area` | 填充面积 | `true` |
| `custom_title` | 自定义标题 | URL 编码文字 |
| `bg_color` | 背景色 | hex 或预设 |
| `line` | 线条颜色 | hex |
| `point` | 点颜色 | hex |
| `color` | 文字颜色 | hex |

## 完整一行命令示例（多卡片并排）

```markdown
<table>
  <tr>
    <td><img src="https://gh-stats.com/api?username={{USERNAME}}&show_icons=true&hide_border=true" width="400" /></td>
    <td><img src="https://gh-stats.com/api/top-langs?username={{USERNAME}}&layout=compact&hide_border=true&langs_count=8" width="400" /></td>
  </tr>
</table>
```
