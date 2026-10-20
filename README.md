# Specialized B2B & Freelance Talent Intelligence Suite

[![Apify Partner](https://img.shields.io/badge/Apify-Official%20Developer%20Partner-0083FE?logo=apify&logoColor=white)](https://apify.com/automation_studio)
[![Category](https://img.shields.io/badge/Category-Contractors%20%26%20Talent-red)](https://apify.com/automation_studio)
[![Scrapers Count](https://img.shields.io/badge/Scrapers%20Included-10%20Production%20Actors-brightgreen)](https://apify.com/automation_studio)
[![Sample Dataset](https://img.shields.io/badge/Dataset-Verified%20CSV%20Sample-success)](./sample_leads.csv)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

Official enterprise monorepo housing **10 production data extraction actors** deployed on [Apify](https://apify.com/automation_studio).

Every scraper in this suite provides accredited member directories, clean decision-maker contacts, real-time listing feeds, and automated exports to CSV, JSON, and Excel.

---

## 🏛️ Included Scrapers Directory (10 Actors)

| Scraper / Actor Title | Capability Overview | Apify Console | Store Page |
|---|---|---|---|
| **StackLead AI - Website Tech Stack & Technology Detector** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/CI8hhTe7rb4W0Ek70) | [Store Page](https://apify.com/automation_studio/website-tech-stack-detector) |
| **HireLead AI - Multi-ATS Job Board Scraper** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/oPDVozDGuqVnAnDdR) | [Store Page](https://apify.com/automation_studio/job-board-scraper) |
| **ContractorLead AI - Thumbtack & Contractor Scraper** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/RXXJU7qKmQeT0JihO) | [Store Page](https://apify.com/automation_studio/thumbtack-contractor-scraper) |
| **InsiderWhale AI - SEC Insider Trading & Whale Alerts (Form 4)** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/ReRoDBdtfXQFtPZdD) | [Store Page](https://apify.com/automation_studio/insider-whale-tracker) |
| **Upwork Enterprise & High-Budget Client Radar (AI Job Sniper)** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/DlUQzIKIxP3we6iD9) | [Store Page](https://apify.com/automation_studio/upwork-enterprise-radar) |
| **SEC Form D Venture Capital Radar (Pre-TechCrunch)** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/AXxecF7hliYy9XT92) | [Store Page](https://apify.com/automation_studio/sec-form-d-venture-capital-radar) |
| **🛡️ GitHub Org Security & Dependency Auditor** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/H9vZx5fihPf12PG5i) | [Store Page](https://apify.com/automation_studio/github-org-security-auditor) |
| **🎯 LinkedIn Job Post ➔ Hiring Manager & Email Extractor** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/UAXMQobdmaHkTpow4) | [Store Page](https://apify.com/automation_studio/linkedin-job-hiring-manager-finder) |
| **Fiverr Pro & Top-Rated Seller Portfolio & Pricing Extractor** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/4WWUEl9kWh9npc8g2) | [Store Page](https://apify.com/automation_studio/fiverr-pro-seller-extractor) |
| **Commercial Construction Subcontractors Scraper** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/2dwXxnZ2V8O0EB54O) | [Store Page](https://apify.com/automation_studio/construction-subcontractors-scraper) |

---

## 🔑 How to Get Your Free Apify API Token

To run any scraper in this suite programmatically or integrate it into your automated sales pipeline:

1. **Sign Up for Free**: Visit [Apify Signup](https://apify.com/) and create a free account. Every new account includes **$5 of free platform credits every month** (enough to run thousands of scrape queries).
2. **Access Your API Settings**: Once logged in, go directly to the [Apify Console Integrations Page](https://console.apify.com/account/integrations).
3. **Copy Your Personal API Token**: Under **API tokens**, click the copy icon next to your **Personal API Token**.
4. **Authenticate in Code**: Pass your token via the `APIFY_TOKEN` environment variable or directly in the client initialization:
   ```python
   from apify_client import ApifyClient
   client = ApifyClient("your_personal_api_token_here")
   ```

---

## ⚡ Quickstart: Programmatic Extraction (Python)

Run any actor from this suite using Python and the official `apify-client` package:

```python
from apify_client import ApifyClient
import pandas as pd

# 1. Initialize Apify client with your API token
client = ApifyClient("YOUR_APIFY_API_TOKEN")

# 2. Run your chosen actor on Apify Cloud
run = client.actor("automation_studio/website-tech-stack-detector").call(
    run_input={
        "maxResults": 500,
        "requireEmail": True
    }
)

# 3. Fetch verified lead items from the default dataset
items = client.dataset(run["defaultDatasetId"]).list_items().items
print(f"Extracted {len(items)} verified records.")

# 4. Save directly to CSV or load into pandas
df = pd.DataFrame(items)
df.to_csv("leads_output.csv", index=False)
```

### Direct cURL Command

```bash
curl -X POST "https://api.apify.com/v2/acts/automation_studio~website-tech-stack-detector/runs?token=YOUR_API_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{"maxResults": 250, "requireEmail": true}'
```

---

## 📊 Sample Dataset Preview

The repository includes [`sample_leads.csv`](./sample_leads.csv) demonstrating the verified 15-column schema:

| Field Name | Type | Description |
|---|---|---|
| `Company Name` | String | Legal corporate or registered trading name |
| `Trade Member ID` | String | Official accreditation identifier or business ID |
| `Primary Email` | String | Validated corporate or sales inquiry email (RFC 5322) |
| `Telephone` | String | Direct business phone with national dialing code (E.164) |
| `Website` | String | Official corporate web address |
| `Street Address` | String | Verified operational facility or corporate headquarters |
| `City` / `State` / `Country` | String | Standardized geographic coordinates |
| `Postal Code` | String | National ZIP or postal routing code |
| `Specializations` | String | Core capabilities and trade tags |
| `Executive Contact` | String | Key decision-maker or managing director |
| `Job Title` | String | Executive functional role |
| `LinkedIn URL` | String | Official corporate LinkedIn profile page |
| `Lead Quality Score` | Integer | Automated composite verification rating (90-100) |

---

## 🛡️ License & Commercial Terms

This repository code is licensed under the [MIT License](./LICENSE). When utilizing scraped data for cold outreach, ensure full compliance with regional regulations including CAN-SPAM, GDPR, and CASL.

- **Developer Profile**: [@automation_studio](https://apify.com/automation_studio)
- **Portfolio Hub**: [asadnaeem828-dev](https://github.com/asadnaeem828-dev)