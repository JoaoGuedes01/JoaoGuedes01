<div align="center">

# João Guedes

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1500&center=true&vCenter=true&width=560&lines=Backend+engineer+%40+Uphold;Distributed+systems+%26+resilience;Security+researcher;Homelab+operator" alt="Backend engineer, distributed systems, security researcher, homelab operator" />

[![Website](https://img.shields.io/badge/joaoguedes.net-0b0b0f?style=for-the-badge&logo=astro&logoColor=white)](https://joaoguedes.net)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/joaom-guedes)
[![Blog](https://img.shields.io/badge/Ramblings-blog-BC52EE?style=for-the-badge)](https://joaoguedes.net/blog)
[![Resume](https://img.shields.io/badge/Resume-CV-2ea44f?style=for-the-badge)](https://joaoguedes.net/resume)
[![Homelab status](https://uptime.joaoguedes.net/api/status-page/status/badge)](https://uptime.joaoguedes.net)

</div>

---

## 👋 About

Backend Engineer at [Uphold](https://uphold.com/), based in Portugal. I design and build distributed backend systems with an emphasis on resilience, observability and maintainability, and my security background lets me look at software the way an attacker would.

Outside of work I run a self-hosted [homelab](#-homelab), which is my playground for systems design, orchestration and security experiments, and I write about it all on [my website](https://joaoguedes.net).

## 🧭 Focus areas

- **Backend & distributed systems**: architecture, workflows, system design
- **Application security**: secure SDLC, vulnerability research, exploit analysis, reverse engineering
- **Platform & DevOps**: orchestration, CI/CD, self-hosted infrastructure

## 🔭 Currently exploring

- 🌐 Growing [joaoguedes.net](https://joaoguedes.net), the v2 of my website (Astro, Tailwind, daisyUI, Cloudflare Pages)
- 📱 AR mobile monster-capturing game (Invizimals-inspired)
- 🎵 Go-based media player
- 🎮 Wii Sports memory analysis + code injection mod
- 🕹️ 2D PSP game with [pspdev](https://pspdev.github.io/)

---

## 🏠 Homelab

A single quiet box running **Proxmox**, ten **LXC containers** and a **ZFS mirror**, treated like a small production environment: least privilege, SSO, backups that get verified, and alerts that reach my phone.

<table>
  <tr>
    <td><b>Hypervisor</b></td><td>Proxmox VE, everything in LXC containers</td>
    <td><b>Storage</b></td><td>ZFS mirror (2 × 8 TB) + NVMe for system and containers</td>
  </tr>
  <tr>
    <td><b>Access</b></td><td>Tailscale / Teleport VPN, Cloudflare Tunnel (no forwarded ports)</td>
    <td><b>Identity</b></td><td>Authentik SSO, Vaultwarden</td>
  </tr>
  <tr>
    <td><b>DNS</b></td><td>Pi-hole + Unbound recursive resolver</td>
    <td><b>Resilience</b></td><td>Proxmox Backup Server, SMART + ZFS scrubs, Uptime Kuma → Discord</td>
  </tr>
</table>

### 🟢 Live status

Real data from my own [Uptime Kuma status page](https://uptime.joaoguedes.net), not a static badge:

| Service | Status | 30-day uptime |
|---|---|---|
| Jellyfin | ![](https://uptime.joaoguedes.net/api/badge/9/status) | ![](https://uptime.joaoguedes.net/api/badge/9/uptime/30d) |
| Navidrome | ![](https://uptime.joaoguedes.net/api/badge/10/status) | ![](https://uptime.joaoguedes.net/api/badge/10/uptime/30d) |
| Seerr | ![](https://uptime.joaoguedes.net/api/badge/11/status) | ![](https://uptime.joaoguedes.net/api/badge/11/uptime/30d) |
| Pi-hole DNS | ![](https://uptime.joaoguedes.net/api/badge/3/status) | ![](https://uptime.joaoguedes.net/api/badge/3/uptime/30d) |

👉 [**Full status page**](https://uptime.joaoguedes.net) · 📐 [**Architecture, security model & roadmap**](home-lab.md) · ✍️ [**The 5-part build story**](https://joaoguedes.net/blog/the-frankenlab)

---

## ✍️ Latest from the blog

<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->

---

## 🛠️ Tech stack

<details open>
<summary><b>Languages & frameworks</b></summary>
<br />

![Go](https://img.shields.io/badge/Go-00ADD8?logo=go&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-5FA04E?logo=nodedotjs&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?logo=openjdk&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?logo=kotlin&logoColor=white)
![C#](https://img.shields.io/badge/C%23-512BD4?logo=dotnet&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?logo=postgresql&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black)
![Astro](https://img.shields.io/badge/Astro-BC52EE?logo=astro&logoColor=white)
![gRPC](https://img.shields.io/badge/gRPC-244C5A?logo=grpc&logoColor=white)
![GraphQL](https://img.shields.io/badge/GraphQL-E10098?logo=graphql&logoColor=white)

</details>

<details>
<summary><b>Data</b></summary>
<br />

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?logo=mongodb&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white)
![DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?logo=amazondynamodb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?logo=redis&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?logo=sqlite&logoColor=white)
![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?logo=elasticsearch&logoColor=white)

</details>

<details>
<summary><b>Infrastructure, networking & observability</b></summary>
<br />

![Temporal](https://img.shields.io/badge/Temporal-000000?logo=temporal&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Proxmox](https://img.shields.io/badge/Proxmox-E57000?logo=proxmox&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?logo=linux&logoColor=black)
![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white)
![Traefik](https://img.shields.io/badge/Traefik-24A1C1?logo=traefikproxy&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?logo=cloudflare&logoColor=white)
![Tailscale](https://img.shields.io/badge/Tailscale-242424?logo=tailscale&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?logo=githubactions&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?logo=jenkins&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?logo=grafana&logoColor=white)

</details>

<details>
<summary><b>Security</b></summary>
<br />

AppSec · DevSecOps · SAST/DAST/SCA · secure coding · pentesting (Burp, ZAP, Nmap, Metasploit)

</details>

## 🎓 Certifications

- **INE eJPT**: Junior Penetration Tester (2025)
- **AWS Cloud DevOps** (2023)

More on [my website](https://joaoguedes.net/certifications).

---

## 🎲 Side projects

| Project | What it is | Link |
|---|---|---|
| **[joaoguedes.net](https://joaoguedes.net)** | My website: projects, blog, snippets and a CV generated from markdown | [Visit](https://joaoguedes.net) |
| **GuedesCrypt** | AES implementation to learn crypto internals | [Try it](https://joaoguedes01.github.io/guedescrypt_ui/) |
| **GuedesMoney** | Automation for Portugal's Finanças portal | [PyPI](https://pypi.org/project/guedesmoney/) |
| **GuedesDB** | Lightweight JSON DB for Node.js | [npm](https://www.npmjs.com/package/guedesdb) |
| **GuedesSueca** | Online Sueca card game over WebSockets | [Play](https://joaoguedes01.github.io/sueca_websocket_client/) |
| **TicTacGuedes** | Reaction / wordplay game | [Play](https://joaoguedes01.github.io/tictacboom/) |
| **FafenseAdventure** | 2D platformer in Unity | [Play](https://joaoguedes01.github.io/FafenseAdventure/) |
| **[nodejs-service-template](https://github.com/JoaoGuedes01/nodejs-service-template)** | Well-structured Node.js service template | [Repo](https://github.com/JoaoGuedes01/nodejs-service-template) |

---

## 📊 GitHub activity

<p align="center">
  <img src="https://streak-stats.demolab.com/?user=JoaoGuedes01&theme=github-dark-blue&hide_border=true" alt="GitHub streak" />
</p>

<p align="center">
  <img height="180" src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=JoaoGuedes01&theme=github_dark" alt="Profile details" />
  <img height="180" src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=JoaoGuedes01&theme=github_dark" alt="Repos per language" />
</p>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/JoaoGuedes01/JoaoGuedes01/output/github-contribution-grid-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/JoaoGuedes01/JoaoGuedes01/output/github-contribution-grid-snake.svg" />
  <img alt="Contribution snake" src="https://raw.githubusercontent.com/JoaoGuedes01/JoaoGuedes01/output/github-contribution-grid-snake.svg" />
</picture>
