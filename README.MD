from pathlib import Path
import shutil, zipfile, textwrap

base = Path("/mnt/data/github_profile_lucas_kiyoshi")
assets = base / "assets"
assets.mkdir(parents=True, exist_ok=True)

# Copy generated icon if available
possible_icon = Path("/mnt/data/desenvolvedor_tech_estilo_chibi_com_ícones.png")
if possible_icon.exists():
    shutil.copy(possible_icon, assets / "profile-icon.png")

# SVG Banner
banner_svg = r'''<svg width="1200" height="360" viewBox="0 0 1200 360" fill="none" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="bg" x1="0" y1="0" x2="1200" y2="360" gradientUnits="userSpaceOnUse">
      <stop offset="0" stop-color="#020617"/>
      <stop offset="0.38" stop-color="#0F172A"/>
      <stop offset="0.70" stop-color="#075985"/>
      <stop offset="1" stop-color="#064E3B"/>
    </linearGradient>
    <radialGradient id="glow1" cx="0" cy="0" r="1" gradientUnits="userSpaceOnUse" gradientTransform="translate(900 120) rotate(90) scale(210)">
      <stop stop-color="#38BDF8" stop-opacity="0.8"/>
      <stop offset="1" stop-color="#38BDF8" stop-opacity="0"/>
    </radialGradient>
    <radialGradient id="glow2" cx="0" cy="0" r="1" gradientUnits="userSpaceOnUse" gradientTransform="translate(260 250) rotate(90) scale(210)">
      <stop stop-color="#22C55E" stop-opacity="0.55"/>
      <stop offset="1" stop-color="#22C55E" stop-opacity="0"/>
    </radialGradient>
    <filter id="shadow" x="-20%" y="-20%" width="140%" height="140%">
      <feDropShadow dx="0" dy="12" stdDeviation="14" flood-color="#000000" flood-opacity="0.35"/>
    </filter>
  </defs>

  <rect width="1200" height="360" rx="30" fill="url(#bg)"/>
  <rect width="1200" height="360" rx="30" fill="url(#glow1)"/>
  <rect width="1200" height="360" rx="30" fill="url(#glow2)"/>

  <g opacity="0.22">
    <path d="M50 290 C220 210, 320 330, 500 240 S820 120, 1140 230" stroke="#38BDF8" stroke-width="2"/>
    <path d="M70 90 C260 170, 360 50, 540 120 S870 270, 1130 90" stroke="#22C55E" stroke-width="2"/>
  </g>

  <g filter="url(#shadow)">
    <rect x="60" y="58" width="1080" height="244" rx="28" fill="#020617" fill-opacity="0.56" stroke="#334155"/>
  </g>

  <g transform="translate(92,88)">
    <rect x="0" y="0" width="156" height="156" rx="34" fill="#0F172A" stroke="#38BDF8" stroke-width="2"/>
    <text x="78" y="62" text-anchor="middle" font-family="Segoe UI, Arial, sans-serif" font-size="32" font-weight="800" fill="#E2E8F0">JFI</text>
    <text x="78" y="96" text-anchor="middle" font-family="Segoe UI, Arial, sans-serif" font-size="15" font-weight="600" fill="#93C5FD">ERP • IA</text>
    <text x="78" y="122" text-anchor="middle" font-family="Segoe UI, Arial, sans-serif" font-size="13" fill="#A7F3D0">CODE HUB</text>
  </g>

  <g transform="translate(292,84)">
    <text x="0" y="46" font-family="Segoe UI, Arial, sans-serif" font-size="48" font-weight="900" fill="#F8FAFC">Lucas Kiyoshi</text>
    <text x="2" y="86" font-family="Segoe UI, Arial, sans-serif" font-size="21" font-weight="600" fill="#BAE6FD">Analista de Sistemas • TOTVS • Dados • Python • IA</text>

    <g transform="translate(0,122)">
      <rect x="0" y="0" width="112" height="34" rx="17" fill="#0EA5E9" fill-opacity="0.2" stroke="#38BDF8"/>
      <text x="56" y="23" text-anchor="middle" font-family="Segoe UI, Arial" font-size="14" font-weight="700" fill="#E0F2FE">ADVPL</text>

      <rect x="126" y="0" width="92" height="34" rx="17" fill="#22C55E" fill-opacity="0.18" stroke="#22C55E"/>
      <text x="172" y="23" text-anchor="middle" font-family="Segoe UI, Arial" font-size="14" font-weight="700" fill="#DCFCE7">TLPP</text>

      <rect x="232" y="0" width="96" height="34" rx="17" fill="#0EA5E9" fill-opacity="0.2" stroke="#38BDF8"/>
      <text x="280" y="23" text-anchor="middle" font-family="Segoe UI, Arial" font-size="14" font-weight="700" fill="#E0F2FE">Fluig</text>

      <rect x="342" y="0" width="122" height="34" rx="17" fill="#22C55E" fill-opacity="0.18" stroke="#22C55E"/>
      <text x="403" y="23" text-anchor="middle" font-family="Segoe UI, Arial" font-size="14" font-weight="700" fill="#DCFCE7">Protheus</text>

      <rect x="478" y="0" width="88" height="34" rx="17" fill="#0EA5E9" fill-opacity="0.2" stroke="#38BDF8"/>
      <text x="522" y="23" text-anchor="middle" font-family="Segoe UI, Arial" font-size="14" font-weight="700" fill="#E0F2FE">RM</text>

      <rect x="580" y="0" width="116" height="34" rx="17" fill="#22C55E" fill-opacity="0.18" stroke="#22C55E"/>
      <text x="638" y="23" text-anchor="middle" font-family="Segoe UI, Arial" font-size="14" font-weight="700" fill="#DCFCE7">Python</text>
    </g>

    <text x="0" y="210" font-family="Consolas, 'Courier New', monospace" font-size="20" fill="#CBD5E1">versionando soluções reais para ERP, automação e inteligência artificial</text>
  </g>

  <g opacity="0.9">
    <circle cx="1034" cy="92" r="5" fill="#38BDF8"/>
    <circle cx="1075" cy="148" r="4" fill="#22C55E"/>
    <circle cx="1010" cy="232" r="3" fill="#FACC15"/>
    <circle cx="1120" cy="262" r="6" fill="#38BDF8"/>
    <circle cx="730" cy="282" r="4" fill="#22C55E"/>
  </g>
</svg>'''
(assets / "banner.svg").write_text(banner_svg, encoding="utf-8")

readme = r'''<div align="center">

<img width="100%" src="./assets/banner.svg" />

<br>

<img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=22&duration=2800&pause=900&center=true&vCenter=true&width=900&lines=Versionando+c%C3%B3digos+ADVPL%2C+TLPP%2C+JS+e+Python;Organizando+solu%C3%A7%C3%B5es+para+Protheus%2C+Fluig+e+RM;Estudando+IA%2C+RAG%2C+automa%C3%A7%C3%B5es+e+dados;Transformando+rotina+t%C3%A9cnica+em+portf%C3%B3lio" />

<br><br>

<img src="https://komarev.com/ghpvc/?username=kiyoshilara&label=PROFILE%20VIEWS&style=for-the-badge&color=0ea5e9" />
<img src="https://img.shields.io/github/followers/kiyoshilara?label=FOLLOWERS&style=for-the-badge&color=22c55e" />
<img src="https://img.shields.io/github/stars/kiyoshilara?label=STARS&style=for-the-badge&color=facc15" />

</div>

<br>

<div align="center">

<table>
  <tr>
    <td width="32%" align="center">
      <img src="./assets/profile-icon.png" width="210" />
      <br><br>
      <strong>ERP Developer Mindset</strong>
      <br>
      <sub>Protheus • Fluig • RM • Dados • IA</sub>
    </td>
    <td width="68%">

## 👋 Olá, eu sou o Lucas

Sou **Analista de Sistemas** com foco em **sistemas corporativos**, atuando principalmente com o ecossistema **TOTVS**, incluindo **Protheus, Fluig e RM**.

Este perfil foi criado para ser meu espaço profissional de **armazenamento, organização e versionamento** de códigos, estudos, consultas, automações e soluções técnicas.

Aqui eu concentro minha evolução em:

- desenvolvimento e manutenção de fontes **ADVPL** e **TLPP**;
- datasets, formulários, eventos e widgets para **Fluig**;
- consultas e integrações envolvendo **Protheus, RM, Oracle e SQL Server**;
- projetos com **JavaScript, HTML, CSS e Python**;
- aplicações práticas com **IA, RAG, agentes e automações**.

  </td>
  </tr>
</table>

</div>

---

<div align="center">

## 🧭 Minha área de atuação

<table>
  <tr>
    <td width="25%" align="center">
      <h3>🧩 Protheus</h3>
      <p>ADVPL, TLPP, relatórios, REST, SmartView, rotinas customizadas e sustentação.</p>
    </td>
    <td width="25%" align="center">
      <h3>🌊 Fluig</h3>
      <p>Datasets, formulários, widgets, eventos, BPM, integrações e SQL Server.</p>
    </td>
    <td width="25%" align="center">
      <h3>🏢 RM</h3>
      <p>Consultas, integrações, apoio técnico, relatórios e análise de dados.</p>
    </td>
    <td width="25%" align="center">
      <h3>🤖 IA & Dados</h3>
      <p>Python, automações, análise de logs, RAG, agentes e bases de conhecimento.</p>
    </td>
  </tr>
</table>

</div>

---

## 🛠️ Tech Stack

<div align="center">

### Linguagens e desenvolvimento

<img src="https://skillicons.dev/icons?i=js,html,css,python,git,github,vscode" />

<br><br>

<img src="https://img.shields.io/badge/ADVPL-0F172A?style=for-the-badge&logo=codeforces&logoColor=38BDF8" />
<img src="https://img.shields.io/badge/TLPP-111827?style=for-the-badge&logo=codeforces&logoColor=22C55E" />
<img src="https://img.shields.io/badge/TOTVS-0EA5E9?style=for-the-badge&logoColor=white" />
<img src="https://img.shields.io/badge/Protheus-003B71?style=for-the-badge&logo=databricks&logoColor=white" />
<img src="https://img.shields.io/badge/Fluig-0284C7?style=for-the-badge&logo=workflow&logoColor=white" />
<img src="https://img.shields.io/badge/RM-2563EB?style=for-the-badge&logo=database&logoColor=white" />

<br><br>

### Banco, dados e automações

<img src="https://skillicons.dev/icons?i=mysql,postgres" />
<img src="https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white" />
<img src="https://img.shields.io/badge/SQL%20Server-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white" />
<img src="https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white" />
<img src="https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=000" />
<img src="https://img.shields.io/badge/IA%20Generativa-020617?style=for-the-badge&logo=openai&logoColor=white" />

</div>

---

<div align="center">

## 📦 Organização dos repositórios

</div>

<table>
  <tr>
    <td width="50%">

### 🟦 `protheus-advpl-tlpp`

```text
📦 protheus-advpl-tlpp
 ┣ 📂 rotinas
 ┣ 📂 relatorios
 ┣ 📂 smartview
 ┣ 📂 pontos-de-entrada
 ┣ 📂 rest-api
 ┗ 📂 utilitarios