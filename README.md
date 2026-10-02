# Restaurant-Tips-Analytics
# Restaurant Tips Analytics Dashboard (with AI Insights)

IBM SkillsBuild – Data Analytics with AI Internship Project

## Project Description
A restaurant owner wants to know **which days earn the most revenue** and **which customers (by time of day and party size) tip best**. This project analyzes restaurant billing data with Python, builds a **one-page interactive dashboard**, and uses **generative AI (Google Gemini)** to turn the numbers into plain-language business insights and a recommendation.

**Flow:** Data → Analysis → AI Insights → One-Page Dashboard

## Dataset
- **Name:** Tips dataset (244 restaurant bills: total bill, tip, day, time, party size, smoker, sex)
- **Link:** https://github.com/mwaskom/seaborn-data/blob/master/tips.csv
- Loaded directly in code with `sns.load_dataset("tips")`, so no manual download is needed.
- No missing values; one column is added: `tip_pct` = tip / total bill × 100.

## Technologies Used
- Python 3
- pandas (data analysis)
- seaborn (dataset loading)
- Plotly (interactive dashboard)
- Google Gemini API via `google-genai` (AI insights)
- Google Colab (development environment)

## Files
| File | Description |
|---|---|
| `YourName_RestaurantTipsDashboard.ipynb` | Complete project code |
| `requirements.txt` | Python dependencies |
| `YourName_ProjectReport.docx` | Full project report |
| `README.md` | This file |

## Setup and Run Instructions (Google Colab)
1. Open [Google Colab](https://colab.research.google.com) and upload `YourName_RestaurantTipsDashboard.ipynb` (File → Upload notebook).
2. Get a free API key from [Google AI Studio](https://aistudio.google.com) (Get API key).
3. In Colab, click the key icon in the left sidebar → **Add new secret** → Name: `GEMINI_KEY`, Value: your key → turn on **Notebook access**.
4. Click **Runtime → Run all**.
5. The dashboard and AI insights appear at the bottom, and `dashboard.html` is saved in the Colab files panel.

### Running locally (optional)
```bash
pip install -r requirements.txt
```
Replace the `userdata.get("GEMINI_KEY")` line with `os.environ["GEMINI_KEY"]` and set that environment variable.

## Key Information
- The AI receives only a **compact text summary**, not the raw data. This is faster, cheaper and more private.
- The AI cell has **retry and model-fallback logic** (handles 503/404 errors). If every model fails, a placeholder message is shown so the dashboard still renders.
- Model names change over time. If you get a 404, list available models with `for m in client.models.list(): print(m.name)` and update the list in Step 4.

## Key Findings
- **Saturday** (about $1,778) and **Sunday** (about $1,627) earn the most; **Friday** (about $326) earns the least.
- **Parties of 1** tip the most (about 21.7%); tip % falls as party size grows.
- Lunch (about 16.4%) and dinner (about 16.0%) tip almost equally.
- Overall: total revenue about $4,828 and an average tip of 16.1%.
