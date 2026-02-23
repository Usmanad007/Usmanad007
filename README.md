<div align="center">

<svg xmlns="http://www.w3.org/2000/svg" width="900" height="240" viewBox="0 0 900 240">
  <defs>
    <linearGradient id="bgGrad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#010810"/>
      <stop offset="45%" style="stop-color:#040e20"/>
      <stop offset="100%" style="stop-color:#071528"/>
    </linearGradient>
    <linearGradient id="nameGrad" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%"   style="stop-color:#38bdf8"/>
      <stop offset="35%"  style="stop-color:#a78bfa"/>
      <stop offset="70%"  style="stop-color:#f472b6"/>
      <stop offset="100%" style="stop-color:#34d399"/>
    </linearGradient>
    <linearGradient id="accentLine" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%"   style="stop-color:transparent"/>
      <stop offset="30%"  style="stop-color:#38bdf8"/>
      <stop offset="70%"  style="stop-color:#a78bfa"/>
      <stop offset="100%" style="stop-color:transparent"/>
    </linearGradient>
    <linearGradient id="topBar" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%"   style="stop-color:#38bdf8"/>
      <stop offset="50%"  style="stop-color:#a78bfa"/>
      <stop offset="100%" style="stop-color:#34d399"/>
    </linearGradient>
    <filter id="glowFilter" x="-20%" y="-20%" width="140%" height="140%">
      <feGaussianBlur stdDeviation="8" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
    <filter id="softGlow" x="-10%" y="-10%" width="120%" height="120%">
      <feGaussianBlur stdDeviation="3" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
    <clipPath id="clip"><rect width="900" height="240" rx="14"/></clipPath>
  </defs>

  <g clip-path="url(#clip)">

    <!-- Background -->
    <rect width="900" height="240" fill="url(#bgGrad)"/>

    <!-- Subtle grid -->
    <g stroke="#38bdf8" stroke-width="0.5" opacity="0.04">
      <line x1="0" y1="60"  x2="900" y2="60"/>
      <line x1="0" y1="120" x2="900" y2="120"/>
      <line x1="0" y1="180" x2="900" y2="180"/>
      <line x1="180" y1="0" x2="180" y2="240"/>
      <line x1="360" y1="0" x2="360" y2="240"/>
      <line x1="540" y1="0" x2="540" y2="240"/>
      <line x1="720" y1="0" x2="720" y2="240"/>
    </g>

    <!-- Ambient glow orbs -->
    <ellipse cx="150" cy="120" rx="200" ry="130" fill="#1e40af" opacity="0.08"/>
    <ellipse cx="750" cy="120" rx="180" ry="120" fill="#4c1d95" opacity="0.1"/>
    <ellipse cx="450" cy="50"  rx="120" ry="80"  fill="#0f766e" opacity="0.07"/>

    <!-- Top gradient bar -->
    <rect x="0" y="0" width="900" height="3" fill="url(#topBar)"/>

    <!-- Corner brackets -->
    <path d="M 0 36 L 0 0 L 36 0"   stroke="#38bdf8" stroke-width="1.5" fill="none" opacity="0.6"/>
    <path d="M 864 0 L 900 0 L 900 36"  stroke="#38bdf8" stroke-width="1.5" fill="none" opacity="0.6"/>
    <path d="M 0 204 L 0 240 L 36 240"  stroke="#38bdf8" stroke-width="1.5" fill="none" opacity="0.6"/>
    <path d="M 864 240 L 900 240 L 900 204" stroke="#38bdf8" stroke-width="1.5" fill="none" opacity="0.6"/>

    <!-- Status indicator -->
    <circle cx="338" cy="62" r="4.5" fill="#34d399">
      <animate attributeName="opacity" values="1;0.2;1" dur="2s" repeatCount="indefinite"/>
    </circle>
    <circle cx="338" cy="62" r="9" fill="#34d399" opacity="0.15">
      <animate attributeName="r" values="6;11;6" dur="2s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0.15;0;0.15" dur="2s" repeatCount="indefinite"/>
    </circle>
    <text x="350" y="67" font-family="'Courier New', monospace" font-size="11" fill="#34d399" opacity="0.85" letter-spacing="1">Available for Opportunities</text>

    <!-- Sliding name — animates from right (x=1100) to final position (x=450) -->
    <text
      x="450" y="148"
      font-family="'Segoe UI', 'Helvetica Neue', sans-serif"
      font-size="58"
      font-weight="900"
      text-anchor="middle"
      fill="url(#nameGrad)"
      filter="url(#glowFilter)"
      letter-spacing="-1.5">
      Muhammad Usman
      <animateTransform
        attributeName="transform"
        type="translate"
        from="650 0"
        to="0 0"
        dur="1.4s"
        fill="freeze"
        calcMode="spline"
        keySplines="0.16 1 0.3 1"/>
      <animate attributeName="opacity" values="0;1" dur="0.5s" fill="freeze"/>
    </text>

    <!-- Horizontal rule -->
    <rect x="250" y="163" width="400" height="1" fill="url(#accentLine)"/>

    <!-- Role subtitle -->
    <text x="450" y="188"
      font-family="'Courier New', monospace"
      font-size="13.5"
      font-weight="400"
      text-anchor="middle"
      fill="#94a3b8"
      letter-spacing="4.5">
      DEVOPS  &amp;  CLOUD  ENGINEER
      <animate attributeName="opacity" values="0;1" dur="1s" begin="0.8s" fill="freeze"/>
    </text>

    <!-- Location tag -->
    <text x="450" y="213"
      font-family="'Courier New', monospace"
      font-size="10"
      text-anchor="middle"
      fill="#475569"
      letter-spacing="2">
      Pakistan  ·  BSc Computer Sciences, University of Okara 2024
      <animate attributeName="opacity" values="0;1" dur="1s" begin="1.1s" fill="freeze"/>
    </text>

    <!-- Bottom gradient bar -->
    <rect x="0" y="237" width="900" height="3" fill="url(#topBar)" opacity="0.35"/>

  </g>
</svg>

</div>

<br/>

<div align="center">

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=15&pause=1000&color=38BDF8&center=true&vCenter=true&width=650&lines=Building+Scalable+Cloud+Infrastructure+on+AWS;Automating+CI%2FCD+Pipelines+with+GitHub+Actions;Containerizing+Workloads+with+Docker;Linux+Administration+%26+Bash+Scripting;GitOps+%7C+Infrastructure+as+Code+%7C+Cloud-Native)](https://git.io/typing-svg)

</div>

---

## About Me

I am a **DevOps & Cloud Engineer** focused on building reliable, scalable, and automated infrastructure. I specialize in bridging development and operations — shipping software faster while keeping systems resilient and observable.

- Architecting and optimizing cloud infrastructure on **AWS**
- Designing **CI/CD pipelines** for fast, zero-downtime software delivery
- Championing **containerization**, **GitOps**, and **Infrastructure as Code** practices

---

## Education

<div align="center">

![University of Okara](https://img.shields.io/badge/University%20of%20Okara-Bachelor%20of%20Computer%20Sciences%20%7C%202024-1a73e8?style=for-the-badge&logo=googlescholar&logoColor=white)

</div>

---

## Tech Stack

### Cloud Platform

![AWS](https://img.shields.io/badge/Amazon%20AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=FF9900)

### Containerization

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

### CI/CD & Automation

![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)

### Version Control

![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)

### Operating System & Scripting

![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)

---

## GitHub Stats

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=YOUR_GITHUB_USERNAME&show_icons=true&theme=github_dark&border_color=30363d&bg_color=0d1117&title_color=38bdf8&icon_color=818cf8&text_color=c9d1d9&hide_border=false&rank_icon=github&include_all_commits=true&count_private=true" height="165"/>
&nbsp;
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=YOUR_GITHUB_USERNAME&layout=compact&theme=github_dark&border_color=30363d&bg_color=0d1117&title_color=38bdf8&text_color=c9d1d9&hide_border=false" height="165"/>

<br/>

<img src="https://streak-stats.demolab.com/?user=YOUR_GITHUB_USERNAME&theme=github-dark-blue&border=30363d&background=0d1117&stroke=38bdf8&ring=38bdf8&fire=f59e0b&currStreakLabel=38bdf8&sideLabels=64748b&dates=8b949e" width="500"/>

</div>

---

## Connect

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/YOUR_LINKEDIN)
&nbsp;
[![Gmail](https://img.shields.io/badge/Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:YOUR_EMAIL)
&nbsp;
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/YOUR_GITHUB_USERNAME)

<br/>

![Profile Views](https://komarev.com/ghpvc/?username=YOUR_GITHUB_USERNAME&color=38bdf8&style=flat-square&label=Profile+Views)

</div>

---

<div align="center">
<sub><b>Muhammad Usman</b> &nbsp;·&nbsp; DevOps & Cloud Engineer &nbsp;·&nbsp; Pakistan</sub>
</div>
