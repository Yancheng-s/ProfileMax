<!--
  模板：仪表盘
  调性：数据密集，Stats 全面展示
  适合：后端工程师、数据工程师、喜欢数据可视化的人
-->

<div align="center">

# {{USERNAME}}

{{BIO}}

{{TYPING_SVG}}

</div>

---

## 关于我

{{ABOUT_ME}}

---

## 技术能力

<div align="center">

{{TECH_STACK_BADGES}}

</div>

---

## 核心指标

<div align="center">

<!-- 第一行：Stats + Streak 并排 -->
<table>
  <tr>
    <td>
      <picture>
        <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username={{USERNAME}}&show_icons=true&count_private=true&theme=onedark&hide_border=true&bg_color=0D1117&rank_icon=github">
        <source media="(prefers-color-scheme: light)" srcset="https://github-readme-stats.vercel.app/api?username={{USERNAME}}&show_icons=true&count_private=true&theme=default&hide_border=true&rank_icon=github">
        <img src="https://github-readme-stats.vercel.app/api?username={{USERNAME}}&show_icons=true&count_private=true&theme=onedark&hide_border=true&bg_color=0D1117&rank_icon=github" width="400" />
      </picture>
    </td>
    <td>
      <picture>
        <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-streak-stats.herokuapp.com/?user={{USERNAME}}&theme=onedark&hide_border=true&background=0D1117">
        <source media="(prefers-color-scheme: light)" srcset="https://github-readme-streak-stats.herokuapp.com/?user={{USERNAME}}&theme=default&hide_border=true">
        <img src="https://github-readme-streak-stats.herokuapp.com/?user={{USERNAME}}&theme=onedark&hide_border=true&background=0D1117" width="400" />
      </picture>
    </td>
  </tr>
</table>

<!-- 第二行：Top Langs + Trophy 并排 -->
<table>
  <tr>
    <td>
      <picture>
        <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/top-langs/?username={{USERNAME}}&layout=compact&theme=onedark&hide_border=true&bg_color=0D1117&langs_count=8">
        <source media="(prefers-color-scheme: light)" srcset="https://github-readme-stats.vercel.app/api/top-langs/?username={{USERNAME}}&layout=compact&theme=default&hide_border=true&langs_count=8">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username={{USERNAME}}&layout=compact&theme=onedark&hide_border=true&bg_color=0D1117&langs_count=8" width="400" />
      </picture>
    </td>
    <td>
      <picture>
        <source media="(prefers-color-scheme: dark)" srcset="https://github-profile-trophy.vercel.app/?username={{USERNAME}}&theme=onedark&no-frame=true&row=2&column=3&margin-w=15&margin-h=15&no-bg=true">
        <source media="(prefers-color-scheme: light)" srcset="https://github-profile-trophy.vercel.app/?username={{USERNAME}}&theme=flat&no-frame=true&row=2&column=3&margin-w=15&margin-h=15&no-bg=true">
        <img src="https://github-profile-trophy.vercel.app/?username={{USERNAME}}&theme=onedark&no-frame=true&row=2&column=3&margin-w=15&margin-h=15&no-bg=true" width="400" />
      </picture>
    </td>
  </tr>
</table>

</div>

---

{{ACTIVITY_GRAPH}}

---

## 精选项目

{{SHOWCASE}}

---

{{BLOG_POSTS}}

---

<div align="center">

{{SOCIAL_LINKS}}

{{VISITOR_COUNTER}}

</div>

<!--
  使用说明：
  1. 表格布局实现卡片并排，充分利用空间
  2. 推荐主题：onedark（暗色）/ default（亮色）
  3. 启用 count_private=true 显示私有仓库贡献
  4. rank_icon=github 在 v2 统计卡片上显示等级
-->
