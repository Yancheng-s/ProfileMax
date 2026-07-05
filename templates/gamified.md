<!--
  模板：游戏化
  调性：奖杯 + Level 概念 + 贡献度游戏化展示
  适合：年轻开发者、开源爱好者、喜欢成就系统的人
-->

<div align="center">

  <h1>
    <img src="https://readme-typing-svg.demolab.com?font=Press+Start+2P&size=22&duration=2000&pause=500&color=A78BFA&center=true&vCenter=true&width=500&lines=PLAYER+ONE;{{USERNAME}}&repeat=true" />
  </h1>

  <p>
    <img src="https://img.shields.io/badge/Level-{{LEVEL}}-brightgreen?style=for-the-badge&logo=level&logoColor=white" />
    <img src="https://img.shields.io/badge/EXP-{{EXP}}-blue?style=for-the-badge&logo=experiment&logoColor=white" />
    <img src="https://img.shields.io/badge/Class-{{CLASS}}-orange?style=for-the-badge&logo=code&logoColor=white" />
  </p>

  <p><em>{{BIO}}</em></p>

</div>

---

### 成就殿堂

<div align="center">

{{TROPHY}}

</div>

---

### 装备（技术栈）

<div align="center">

{{TECH_STACK_ICONS}}

</div>

---

### 角色属性

<div align="center">

<!-- 属性面板 -->
<table>
  <tr>
    <th>HP</th>
    <td>
      <img src="https://gh-stats.com/api?username={{USERNAME}}&show_icons=true&count_private=true&hide_border=true" width="380" />
    </td>
  </tr>
  <tr>
    <th>ATK</th>
    <td>
      <img src="https://github-readme-streak-stats.herokuapp.com/?user={{USERNAME}}&theme=dracula&hide_border=true&background=1A1B27" width="380" />
    </td>
  </tr>
  <tr>
    <th>INT</th>
    <td>
      <img src="https://gh-stats.com/api/top-langs?username={{USERNAME}}&layout=compact&hide_border=true&langs_count=10" width="380" />
    </td>
  </tr>
</table>

</div>

---

### 最近活动地图

{{ACTIVITY_GRAPH}}

---

### 任务日志（最新博文）

{{BLOG_POSTS}}

---

### 装备库（项目）

{{SHOWCASE}}

---

<div align="center">

<img src="https://raw.githubusercontent.com/{{USERNAME}}/{{USERNAME}}/output/github-contribution-grid-snake-dark.svg" />

</div>

---

<div align="center">

{{SOCIAL_LINKS}}

{{VISITOR_COUNTER}}

</div>

<!--
  使用说明：
  1. {{LEVEL}}、{{EXP}}、{{CLASS}} 是自定义的"游戏化"属性
     - LEVEL: 根据账号活跃度给个 Lv.1-100
     - EXP: 根据总提交数给个经验值表述
     - CLASS: 职业身份，比如 Developer、Code Wizard 等
  2. 贪吃蛇需要配置 .github/workflows/snake.yml
  3. 推荐主题：dracula 或 radical，跟游戏风格搭配
-->
