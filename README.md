# shelby-analytics-dashboard

> Real-time analytics dashboard for Shelby Protocol storage metrics and Aptos on-chain data.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Shelby](https://img.shields.io/badge/Shelby-Protocol-22D3A5?style=flat-square&labelColor=0a0a0f)
![Aptos](https://img.shields.io/badge/Aptos-L1-blue?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-white?style=flat-square)

## Overview

`shelby-analytics-dashboard` is a Python-based CLI and web dashboard that aggregates real-time metrics from the Shelby Protocol and Aptos blockchain. Track storage usage, blob activity, account balances, transaction history, and storage costs all in one place.

Built as a companion tool for [BlobSafe](https://github.com/0xPevita/blobsafe).

## Features

- **Real-time blob metrics** - total blobs, sizes, expiry dates per account
- **On-chain transaction history** - filter by Shelby storage events
- **Cost analytics** - ShelbyUSD spent per day/week/month
- **Expiry alerts** - warn when blobs are about to expire
- **Storage trends** - visualize growth over time
- **Multi-account support** - monitor multiple Aptos addresses at once
- **Export reports** - CSV and JSON output for further analysis

## Requirements

- Python 3.9+
- pip packages: `requests`, `rich`, `typer`, `pandas`, `matplotlib`

## Installation
```bash
git clone https://github.com/0xPevita/shelby-analytics-dashboard.git
cd shelby-analytics-dashboard
pip install -r requirements.txt
```

## Usage
```bash
# Show dashboard for an account
python main.py dashboard 0xYourAddress

# Show blob list with sizes and expiry
python main.py blobs 0xYourAddress

# Show transaction history (Shelby events only)
python main.py txns 0xYourAddress --limit 20

# Show cost report (last 30 days)
python main.py costs 0xYourAddress --days 30

# Check for expiring blobs (next 7 days)
python main.py alerts 0xYourAddress --days 7

# Export data to CSV
python main.py export 0xYourAddress --format csv --output report.csv

# Monitor multiple accounts
python main.py monitor 0xAddr1 0xAddr2 0xAddr3
```

## Example Output
╔══════════════════════════════════════════════════════╗
║         SHELBY ANALYTICS DASHBOARD v1.0.0           ║
║         Account: 0x7271...d042                       ║
╚══════════════════════════════════════════════════════╝
📦 STORAGE OVERVIEW
Total blobs:      24
Total size:       128.4 MB
Encrypted:        20 (83%)
Public:           4 (17%)
Expiring (7d):    3 ⚠️
💰 COST SUMMARY
Total spent:      12.45 ShelbyUSD
This month:       3.20 ShelbyUSD
Avg per blob:     0.52 ShelbyUSD
⛓️  RECENT ACTIVITY
2025-03-10  register_blob   report.pdf       0.45 sUSD
2025-03-09  register_blob   dataset.zip      1.20 sUSD
2025-03-08  register_blob   backup.tar.gz    0.98 sUSD

## Architecture
shelby-analytics-dashboard/
├── main.py              # CLI entry point (Typer)
├── dashboard/
│   ├── init.py
│   ├── fetcher.py       # API calls to Shelby + Aptos
│   ├── analyzer.py      # Data processing and metrics
│   ├── renderer.py      # Rich terminal UI rendering
│   ├── alerts.py        # Expiry and threshold alerts
│   └── exporter.py      # CSV/JSON export
├── config/
│   ├── init.py
│   └── settings.py      # API endpoints and defaults
├── requirements.txt
└── .env.example

## Configuration

Copy `.env.example` to `.env` and configure:
```env
SHELBY_API_URL=https://api.shelbynet.shelby.xyz/shelby/v1
APTOS_API_URL=https://api.testnet.aptoslabs.com/v1
APTOS_API_KEY=aptoslabs_your_key_here
```

## Related Projects

- [BlobSafe](https://github.com/0xPevita/blobsafe) - Decentralized encrypted storage dApp
- [shelby-s3-sync](https://github.com/0xPevita/shelby-s3-sync) - S3 sync tool
- [aptos-account-scanner](https://github.com/0xPevita/aptos-account-scanner) - Account scanner

## License

MIT
Commit: docs: add README
