from pathlib import Path
from PIL import Image, ImageDraw, ImageFont
import shutil, zipfile, textwrap

base = Path("/mnt/data/github_profile_lucasjfi_v3_limpo")
assets = base / "assets"
assets.mkdir(parents=True, exist_ok=True)

# Copy generated avatar/icon if exists
source_icon = Path("/mnt/data/desenvolvedor_tech_estilo_chibi_com_ícones.png")
if source_icon.exists():
    shutil.copy(source_icon, assets / "avatar-github.png")

# Create a clean PNG banner to avoid SVG rendering/code issues
banner = Image.new("RGB", (1400, 420), (10, 15, 25))
draw = ImageDraw.Draw(banner)

# gradient background
for x in range(1400):
    r = int(8 + (x / 1400) * 5)
    g = int(13 + (x / 1400) * 55)
    b = int(25 + (x / 1400) * 75)
    draw.line([(x, 0), (x, 420)], fill=(r, g, b))

# soft circles
for bbox, color in [
    ((920, -140, 1320, 260), (25, 120, 180)),
    ((-100, 220, 340, 650), (30, 140, 100)),
    ((580, 130, 1040, 590), (20, 80, 140)),
]:
    overlay = Image.new("RGBA", banner.size, (0,0,0,0))
    od = ImageDraw.Draw(overlay)
    od.ellipse(bbox, fill=color+(90,))
    banner = Image.alpha_composite(banner.convert("RGBA"), overlay).convert("RGB")
    draw = ImageDraw.Draw(banner)

# Card
draw.rounded_rectangle((70, 60, 1330, 350), radius=34, fill=(5, 10, 22), outline=(70, 90, 120), width=2)

# JFI placeholder block
draw.rounded_rectangle((105, 105, 315, 305), radius=30, fill=(15, 23, 42), outline=(56, 189, 248), width=3)

try:
    font_big = ImageFont.truetype("DejaVuSans-Bold.ttf", 62)
    font_mid = ImageFont.truetype("DejaVuSans-Bold.ttf", 36)
    font_small = ImageFont.truetype("DejaVuSans.ttf", 25)
    font_mono = ImageFont.truetype("DejaVuSansMono.ttf", 24)
except:
    font_big = font_mid = font_small = font_mono = None

draw.text((210, 170), "JFI", fill=(240,248,255), anchor="mm", font=font_big)
draw.text((210, 226), "ERP • IA", fill=(125,211,252), anchor="mm", font=font_small)

draw.text((365, 138), "Lucas Kiyoshi", fill=(248,250,252), font=font_big)
draw.text((368, 205), "Analista de Sistemas • TOTVS • Dados • Python • IA", fill=(186,230,253), font=font_small)
draw.text((368, 258), "ADVPL • TLPP • Protheus • Fluig • RM • SQL • Automação", fill=(209,250,229), font=font_mono)

# small decorative code lines
for i, txt in enumerate(["</>", "{ ERP }", "SELECT *", "AI + DATA", "GIT"]):
    x = 980 + (i%2)*140
    y = 95 + i*45
    draw.rounded_rectangle((x, y, x+115, y+30), radius=14, fill=(15, 23, 42), outline=(30, 80, 110), width=1)
    draw.text((x+57, y+19), txt, fill=(125,211,252), anchor="mm", font=ImageFont.truetype("DejaVuSansMono.ttf", 15) if font_mono else None)

banner.save(assets / "banner.png")

# JFI logo placeholder png
jfi = Image.new("RGBA", (500, 260), (0, 0, 0, 0))
jd = ImageDraw.Draw(jfi)
jd.rounded_rectangle((10, 10, 490, 250), radius=28, fill=(15,23,42,255), outline=(56,189,248,255), width=4)
jd.text((250, 105), "JFI", fill=(248,250,252,255), anchor="mm", font=font_big)
jd.text((250, 165), "substitua pela logo oficial", fill=(147,197,253,255), anchor="mm", font=font_small)
jfi.save(assets / "jfi-logo.png")

readme = r'''<div align="center">

<img width="100%" src="./assets/banner.png" />

<br><br>

<img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=21&duration=2700&pause=900&center=true&vCenter=true&width=900&lines=Versionando+fontes+ADVPL%2C+TLPP%2C+JS+e+Python;Organizando+solu%C3%A7%C3%B5es+para+Protheus%2C+Fluig+e+RM;ERP+%2B+Dados+%2B+Automa%C3%A7%C3%A3o+%2B+IA;Transformando+rotina+t%C3%A9cnica+em+portf%C3%B3lio" />

<br><br>

<img src="https://komarev.com/ghpvc/?username=lucasjfi&label=PROFILE%20VIEWS&style=for-the-badge&color=0ea5e9" />
<img src="https://img.shields.io/github/followers/lucasjfi?label=FOLLOWERS&style=for-the-badge&color=22c55e" />
<img src="https://img.shields.io/github/stars/lucasjfi?label=STARS&style=for-the-badge&color=facc15" />

</div>

---

<table>
  <tr>
    <td width="32%" align="center">
      <img src="./assets/avatar-github.png" width="230" />
      <br><br>
      <strong>ERP Code Hub</strong>
      <br>
      <sub>Protheus • Fluig • RM • Python • IA</sub>
    </td>
    <td width="68%">

## 👋 Sobre mim

Sou **Lucas Kiyoshi**, Analista de Sistemas com atuação em sistemas corporativos, principalmente no ecossistema **TOTVS**.

Este perfil é meu espaço profissional para **armazenar, organizar e versionar códigos** usados em estudos, sustentação, automações e desenvolvimento de soluções para ERP.

Atualmente meu foco está em:

- **ADVPL** e **TLPP** para Protheus;
- **JavaScript, HTML e CSS** para Fluig;
- **SQL Server** e **Oracle** para consultas, relatórios e integrações;
- **Python** para automações, dados e análise de logs;
- **IA, RAG e agentes** aplicados a problemas reais de operação.

  </td>
  </tr>
</table>

---

<div align="center">

## 🧩 Ecossistema principal

<table>
  <tr>
    <td align="center" width="25%">
      <h3>🟦 Protheus</h3>
      <p>ADVPL, TLPP, SmartView, relatórios, rotinas, REST e Oracle.</p>
    </td>
    <td align="center" width="25%">
      <h3>🟨 Fluig</h3>
      <p>Datasets, forms, widgets, eventos, BPM, JavaScript e SQL Server.</p>
    </td>
    <td align="center" width="25%">
      <h3>🟩 RM</h3>
      <p>Consultas, integrações, apoio técnico, relatórios e análise de dados.</p>
    </td>
    <td align="center" width="25%">
      <h3>🤖 IA & Dados</h3>
      <p>Python, automações, logs, RAG, agentes e bases de conhecimento.</p>
    </td>
  </tr>
</table>

</div>

---

<div align="center">

## 🛠️ Minhas stacks

### Desenvolvimento

<img src="https://skillicons.dev/icons?i=js,html,css,python,git,github,vscode" />

<br><br>

<img src="https://img.shields.io/badge/ADVPL-0D1117?style=for-the-badge&logo=codeforces&logoColor=38BDF8" />
<img src="https://img.shields.io/badge/TLPP-0D1117?style=for-the-badge&logo=codeforces&logoColor=22C55E" />
<img src="https://img.shields.io/badge/TOTVS-0EA5E9?style=for-the-badge&logoColor=white" />
<img src="https://img.shields.io/badge/Protheus-003B71?style=for-the-badge&logo=databricks&logoColor=white" />
<img src="https://img.shields.io/badge/Fluig-0284C7?style=for-the-badge&logo=workflow&logoColor=white" />
<img src="https://img.shields.io/badge/RM-2563EB?style=for-the-badge&logo=database&logoColor=white" />

<br><br>

### Dados, automação e IA

<img src="https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white" />
<img src="https://img.shields.io/badge/SQL%20Server-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white" />
<img src="https://img.shields.io/badge/SQL-334155?style=for-the-badge&logo=postgresql&logoColor=white" />
<img src="https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white" />
<img src="https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=000" />
<img src="https://img.shields.io/badge/IA%20Generativa-111827?style=for-the-badge&logo=openai&logoColor=white" />

</div>

---

## 📁 Organização dos repositórios

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