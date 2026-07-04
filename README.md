<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,25:203A43,50:2C5364,75:1A5276,100:0F2027&height=220&section=header&text=FloatChart%20🌊&fontSize=70&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Ask%20the%20ocean%20a%20question.%20Get%20an%20answer%20in%20seconds.&descSize=18&descAlignY=62&descAlign=50" width="100%"/>

<br/>

<img src="https://img.shields.io/badge/Ocean_Records-46M+-0F2027?style=for-the-badge&labelColor=203A43" alt="Records"/>
<img src="https://img.shields.io/badge/ARGO_Floats-4000+-2C5364?style=for-the-badge&labelColor=1A5276" alt="Floats"/>
<img src="https://img.shields.io/badge/API-Agent_Ready-16a34a?style=for-the-badge&labelColor=15803d" alt="Agent Ready"/>
<img src="https://img.shields.io/badge/Runs-100%25_Offline-f59e0b?style=for-the-badge&labelColor=b45309" alt="Offline"/>

<br/><br/>

<img src="https://img.shields.io/badge/Python-3.9+-3776AB?style=flat-square&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/Flask-2.0+-000000?style=flat-square&logo=flask&logoColor=white"/>
<img src="https://img.shields.io/badge/PostgreSQL-15+-316192?style=flat-square&logo=postgresql&logoColor=white"/>
<img src="https://img.shields.io/badge/Leaflet.js-Maps-199900?style=flat-square&logo=leaflet&logoColor=white"/>
<img src="https://img.shields.io/badge/Chart.js-Visualizations-FF6384?style=flat-square&logo=chartdotjs&logoColor=white"/>
<img src="https://img.shields.io/badge/License-MIT-22c55e?style=flat-square"/>

</div>

<br/>

<div align="center">
<img src="assets/dashboard.png" width="92%" alt="FloatChart Dashboard" style="border-radius: 14px; box-shadow: 0 10px 30px rgba(0,0,0,0.45);">
</div>

<br/>

## 🎯 What is this?

**FloatChart** turns the ARGO ocean observation network — 4,000+ autonomous floats, 46 million+ profiles of temperature, salinity, and depth — into something you can just *talk to*. No SQL, no NetCDF wrangling, no oceanography degree. Ask a question in plain English, get back a chart, a map, or a clean export.

> *"Show temperature trends in the Bay of Bengal for 2024"* → done in under a second.

<table width="100%">
<tr>
<td width="20%" align="center">🔓<br/><b>Open</b></td>
<td width="20%" align="center">🤖<br/><b>Agent-Ready</b></td>
<td width="20%" align="center">📴<br/><b>Offline-First</b></td>
<td width="20%" align="center">🔒<br/><b>Privacy-First</b></td>
<td width="20%" align="center">🛡️<br/><b>Safety-First</b></td>
</tr>
<tr>
<td align="center"><sub>All data & code publicly accessible</sub></td>
<td align="center"><sub>Versioned REST API built for LLMs</sub></td>
<td align="center"><sub>Runs fully on-device after setup</sub></td>
<td align="center"><sub>Zero telemetry, zero tracking</sub></td>
<td align="center"><sub>7-layer SQL sanitizer on every query</sub></td>
</tr>
</table>

---

## 🏗️ How it fits together

<div align="center">
<img src="assets/architecture.png" width="92%" alt="FloatChart Architecture" style="border-radius: 14px; box-shadow: 0 10px 30px rgba(0,0,0,0.45);">
</div>

---

## ✨ What you get

<table>
<tr>
<td width="50%" valign="top">

### 💬 AI Chat Interface
Natural language → SQL → chart, automatically.
- 7 query types: statistics, proximity, profiles & more
- Instant AI-written summaries
- One-click CSV export

</td>
<td width="50%" valign="top">

### 🗺️ Live Ocean Map
Click anywhere on Earth's oceans.
- Nearby floats surface instantly
- Real-time trajectory playback
- Date-range filtering + hover details

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 📊 Analytics Dashboard
Pre-built views for real analysis.
- Temperature time series
- Salinity distributions
- Vertical depth profiles

</td>
<td width="50%" valign="top">

### 🤖 Developer API
Everything above, callable from code.
- `POST /api/v1/query`
- `GET /api/v1/tools` — agent manifest
- Sub-second responses, no auth needed locally

</td>
</tr>
</table>

---

## ⚡ Quick Start

```bash
git clone <your-repo-url>
cd FloatChart

python local_setup.py   # installs deps, configures DB, launches app
```

Opens automatically at **`http://localhost:5000`** 🎉

<details>
<summary><b>🔑 Prerequisites</b></summary>

<br/>

| Service | Cost | Get a key |
|:--|:--|:--|
| NVIDIA NIM | Varies | [build.nvidia.com](https://build.nvidia.com) |
| DeepSeek *(optional)* | Cheap | [platform.deepseek.com](https://platform.deepseek.com/) |

</details>

<details>
<summary><b>⚙️ Configuration (.env)</b></summary>

<br/>

```env
DATABASE_URL=postgresql://postgres:YOUR_PASSWORD@localhost:5432/floatchart
NVIDIA_API_KEY=nvapi-xxxxxxxxxxxxxxxxxxxxxxxx
NVIDIA_MODEL=meta/llama-3.3-70b-instruct

# Optional providers
# ANTHROPIC_API_KEY=sk-ant-...
# OPENAI_API_KEY=sk-...
# DEEPSEEK_API_KEY=...
```

</details>

---

## 🤖 Developer API

```bash
curl -X POST http://localhost:5000/api/v1/query \
  -H "Content-Type: application/json" \
  -d '{"query": "Show average temperature in Bay of Bengal for 2024"}'
```

```json
{
  "success":      true,
  "answer":       "Average temperature in Bay of Bengal (2024): 28.4°C based on 3,201 measurements.",
  "chart_type":   "line",
  "query_type":   "Time-Series",
  "record_count": 365,
  "elapsed_ms":   218.4
}
```

<div align="center">

| Method | Endpoint | Description |
|:--|:--|:--|
| `POST` | `/api/v1/query` | Natural language → structured ocean data |
| `GET`  | `/api/v1/tools` | Machine-readable tool manifest for agents |
| `POST` | `/api/v1/validate-sql` | Run the safety sanitizer manually |
| `GET`  | `/api/health` | Health check + DB status |
| `GET`  | `/api/stats` | Database statistics |

</div>

**From Python:**
```python
import requests

def ask_ocean(question: str) -> dict:
    r = requests.post("http://localhost:5000/api/v1/query",
                       json={"query": question, "max_rows": 500})
    return r.json()

print(ask_ocean("Find the 5 nearest floats to Chennai")["answer"])
```

**Built for agents:** every tool is auto-discoverable via `curl http://localhost:5000/api/v1/tools`, so LLM agents (including anything speaking MCP) can call `query_ocean_data`, `get_temperature_trend`, `get_depth_profile`, and more without hand-written glue code.

---

## 🛡️ Safety Layer

Every AI-generated SQL query is checked before it ever reaches the database:

<div align="center">

| # | Layer | Blocks |
|:-:|:--|:--|
| 1 | Allowlist | Anything that isn't `SELECT` / `WITH` |
| 2 | Keyword scan | `DROP`, `DELETE`, `INSERT`, `UPDATE`, `TRUNCATE`, `ALTER`, `GRANT` |
| 3 | No stacking | `;`-chained injection attempts |
| 4 | No comment tricks | `--` and `/* */` bypasses |
| 5 | LIMIT cap | Runaway million-row queries |
| 6 | No system abuse | `pg_read_file`, `pg_sleep`, `COPY` |
| 7 | Clear rejections | Every block returns a human-readable reason |

</div>

```python
from sql_sanitizer import SQLSanitizer

SQLSanitizer.validate("SELECT AVG(temperature) FROM argo_data")
# → {"safe": True}

SQLSanitizer.validate("DROP TABLE argo_data;")
# → {"safe": False, "reason": "Blocked keyword detected: DROP"}
```

---

## 📁 Project Layout

```
FloatChart/
├── ARGO_CHATBOT/          # Main app — Flask server, LLM brain, SQL builder + sanitizer
│   └── static/            # Chat UI · Map UI · Dashboard UI
├── DATA_GENERATOR/        # Local ERDDAP data ingestion tool
├── local_setup.py         # One-click setup wizard
├── requirements.txt
├── .env.example
└── CONTRIBUTING.md
```

---

## 🛠️ Tech Stack

<div align="center">

| Layer | Technology |
|:-:|:--|
| Backend | Python 3.9+ · Flask 2.0+ |
| AI / LLM | NVIDIA Llama 3.3 70B · DeepSeek · OpenAI · Claude · Gemini |
| Database | PostgreSQL 15+ · SQLAlchemy |
| Frontend | HTML5 · CSS3 · JavaScript |
| Visualization | Chart.js · Leaflet.js |

</div>

---

## 📚 Resources

<div align="center">

| Resource | Link |
|:-:|:--|
| 🌊 ARGO Program | [argo.ucsd.edu](https://argo.ucsd.edu) |
| 📡 ERDDAP Server | [erddap.ifremer.fr](https://erddap.ifremer.fr) |
| 🧠 NVIDIA NIM | [build.nvidia.com](https://build.nvidia.com) |
| 🤝 Contributing | [CONTRIBUTING.md](./CONTRIBUTING.md) |

</div>

---

## 📄 License

MIT — free to use, modify, and distribute. See [LICENSE](LICENSE).

<br/>

<div align="center">
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,25:203A43,50:2C5364,75:1A5276,100:0F2027&height=110&section=footer" width="100%"/>

<i>The open intelligence layer for ARGO ocean data</i> 🌊
</div>
