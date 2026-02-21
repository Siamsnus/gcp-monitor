# Global Consciousness Monitor

Real-time visualization of the [Global Consciousness Project](https://global-mind.org/) (GCP) random number generator network.

## How It Works

- **Frontend**: Static HTML/CSS/JS hosted on GitHub Pages
- **Data**: JSON file updated every 10 minutes via GitHub Actions
- **Source**: GCP Dot (gcpdot.com) real-time coherence data
- **Cost**: $0 — runs entirely on GitHub free tier

## Setup

1. **Fork this repo** (or create a new one and copy these files)

2. **Enable GitHub Pages**:
   - Go to Settings → Pages
   - Source: Deploy from branch
   - Branch: `main`, folder: `/ (root)`
   - Save

3. **Enable GitHub Actions**:
   - Go to Actions tab
   - Enable workflows
   - The `Fetch GCP Data` workflow will run automatically every 10 minutes

4. **Custom domain** (optional):
   - Add a `CNAME` file with your domain
   - Configure DNS at your registrar

## Files

```
├── index.html              # Main site (single-file, no build step)
├── fetch_gcp_data.py       # Python script run by GitHub Actions
├── data/
│   ├── gcp-current.json    # Current data (auto-updated)
│   └── gcp-history.json    # Rolling 24h history (auto-updated)
└── .github/
    └── workflows/
        └── fetch-gcp-data.yml  # Scheduled data fetcher
```

## Data Sources

- **GCP Dot** (gcpdot.com) — Real-time network coherence, updates every minute
- **GCP Raw Data** (global-mind.org) — Daily CSV files with per-second, per-egg data
- **GCP 2.0** (gcp2.net) — Newer HeartMath network with 300+ devices

Currently using GCP Dot for real-time data. The fetcher can be extended to pull daily CSV files for richer historical analysis.

## Extending

### Adding daily CSV data
The `fetch_gcp_data.py` script can be extended to download daily CSV files from:
```
https://global-mind.org/data/eggsummary/YYYY/basketdata-YYYY-MM-DD.csv.gz
```
This would give per-egg, per-second data for deeper analysis.

### Combining with Schumann Resonance
Add a cross-reference link or combined view showing both GCP network variance and Schumann resonance data on the same timeline.

## Credits

- Data: [Global Consciousness Project](https://global-mind.org/), Princeton
- GCP Dot: [gcpdot.com](https://gcpdot.com/)
- This is an independent visualization, not affiliated with Princeton University or the GCP.
