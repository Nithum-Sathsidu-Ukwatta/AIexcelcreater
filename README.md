# Cell Outage – Required Spares Analyzer

A **single-page web app** (`index.html`) that:

- 📂 Uploads a cell outage Excel file (.xlsx / .xls / .csv)
- 🔍 Automatically filters rows where the **Remarks** column mentions spare parts (e.g. "No spares 900 RRU", "BBU", "RRU", etc.)
- 📊 Shows interactive **charts** (by vendor, region, technology, duration breakdown)
- 📈 Tracks **history** across multiple uploads and shows a trend chart
- 🤖 Runs **AI analysis** via [OpenRouter](https://openrouter.ai) (free models available) to suggest which spares to procure and in what priority
- 📥 **Exports a styled Excel** (.xlsx) with colour-coded rows, a dedicated **Spares Needed** sheet, a summary sheet, and full history
- 📄 **Exports an HTML report** for easy sharing / printing

## How to Use

1. **Open `index.html`** in any modern browser (no server needed – it runs entirely client-side).

2. **Configure OpenRouter API key (app owner step)**:
   - Get a free key from <https://openrouter.ai/keys> (free tier available).
   - Configure `window.OPENROUTER_API_KEY` (or a secure fallback in code) before sharing the app with end users.

3. **Upload your Excel file** (drag & drop or click *Browse File*).  
   The expected columns are:  
   `ID | Vendor | Tech | Site ID | Site Name | Cell | Region | Down On | Duration (Days) | Reported By | Reported To | Remarks`

4. The app automatically shows only rows where spares are needed (**"required spares only"**).  
   A row is included if its **Remarks** column contains any of these keywords (case-insensitive):  
   `spare`, `rru`, `bbu`, `antenna`, `cable`, `module`, `card`, `unit`, `hardware`, `equipment`

5. Use the **filter bar** to search / narrow down by vendor, region, or technology.

6. Click **Run AI Analysis** to get AI-powered procurement recommendations.

7. Click **Export Excel** or **Export HTML Report** to download the styled output.

## Colour Coding

| Colour | Duration |
|--------|----------|
| 🔴 Red | > 60 days (Critical) |
| 🟠 Orange | 31–60 days (High) |
| 🟡 Yellow | ≤ 30 days (Medium) |

## Technologies Used

| Library | Purpose |
|---------|---------|
| [SheetJS (xlsx)](https://sheetjs.com) | Parse & export Excel files |
| [Chart.js](https://chartjs.org) | Interactive charts |
| [Bootstrap 5](https://getbootstrap.com) | UI layout & styling |
| [OpenRouter API](https://openrouter.ai) | Free AI analysis |

All libraries are loaded from CDN – no `npm install` required.
