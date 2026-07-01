<!--
  模板：创意·卡片
  调性：波浪头图 + 自定义布局，视觉冲击力强
  适合：喜欢视觉个性、想与众不同的开发者
-->

<div align="center">

  <!-- 动态波浪头图 -->
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://capsule-render.vercel.app/api?type=rect&color=gradient&customColorList=0,2,4,6,12,20&height=180&section=header&text=Hi+%F0%9F%91%8B+I'm+{{USERNAME}}&fontSize=45&fontAlignY=45&animation=fadeIn">
    <source media="(prefers-color-scheme: light)" srcset="https://capsule-render.vercel.app/api?type=rect&color=gradient&customColorList=0,2,4,6,12,20&height=180&section=header&text=Hi+%F0%9F%91%8B+I'm+{{USERNAME}}&fontSize=45&fontAlignY=45&animation=fadeIn">
    <img src="https://capsule-render.vercel.app/api?type=rect&color=gradient&customColorList=0,2,4,6,12,20&height=180&section=header&text=Hi+%F0%9F%91%8B+I'm+{{USERNAME}}&fontSize=45&fontAlignY=45&animation=fadeIn" />
  </picture>

  <!-- 打字动画 -->
  {{TYPING_SVG}}

</div>

---

<!-- 关于我 — 卡片风格 -->
<div align="center">
  <table>
    <tr>
      <td width="200" align="center">
        <img src="https://github.com/{{USERNAME}}.png" width="150" style="border-radius: 50%; border: 3px solid #A78BFA;" />
        <br/>
        <strong>{{USERNAME}}</strong>
        <br/>
        <em>{{BIO}}</em>
      </td>
      <td width="500" align="left">
        <h3>关于我</h3>
        {{ABOUT_ME}}
      </td>
    </tr>
  </table>
</div>

---

### 我用的工具

<div align="center">

{{TECH_STACK_ICONS}}

<br/>

{{TECH_STACK_BADGES}}

</div>

---

### 开发统计

<div align="center">

  <!-- 三列卡片布局 -->
  <table>
    <tr>
      <td align="center"><strong>⭐ 总 Stars</strong></td>
      <td align="center"><strong>连续提交</strong></td>
      <td align="center"><strong>常用语言</strong></td>
    </tr>
    <tr>
      <td>{{GITHUB_STATS}}</td>
      <td>{{STREAK}}</td>
      <td>{{TOP_LANGS}}</td>
    </tr>
  </table>

</div>

---

<div align="center">

  <details>
    <summary>点击展开成就奖杯</summary>
    <br/>
    {{TROPHY}}
  </details>

</div>

---

{{ACTIVITY_GRAPH}}

---

{{BLOG_POSTS}}

---

{{SHOWCASE}}

---

<div align="center">

{{SOCIAL_LINKS}}

{{SNAKE}}

{{VISITOR_COUNTER}}

</div>

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=rect&color=gradient&customColorList=0,2,4,6,12,20&height=80&section=footer&text=Thanks+for+visiting!&fontSize=20&fontAlignY=50" />
</div>

<!--
  使用说明：
  1. 头像用了 GitHub 自动生成的 .png 链接 (https://github.com/USERNAME.png)
  2. 奖杯默认折叠，用户可点击展开，保持主页整洁
  3. 统计卡片推荐主题：catppuccin_latte（亮）或 catppuccin_mocha（暗）
  4. 渐变颜色的 customColorList 值可以调出不同效果
-->
