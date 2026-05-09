---
name: python-setup
description: Analyze your Python project needs and provide a customized setup with exact packages required. Guides beginners on what tools they actually need.
---

# Python Setup Skill

## What This Does

You describe what you want to build. This skill analyzes your needs and:

1. **Explains what you need** — tells you which packages (Beautiful Soup, Selenium, Pandas, etc.) are actually required for YOUR task
2. **Explains what you DON'T need** — skips unnecessary packages
3. **Creates a setup** — generates a customized `requirements.txt` with ONLY what you need
4. **Provides ONE command** — gives you a single setup command to start immediately
5. **Guides you step-by-step** — explains how to use each package for your specific task

## How to Use This Skill

Simply describe your Python project task. Examples:

```
I want to scrape data from an e-commerce website and save product prices to a CSV file
```

```
I need to automate clicking through a website that loads content with JavaScript
```

```
I want to download images from a website and organize them by category
```

```
I need to monitor a website for price changes and send alerts
```

## What The Skill Provides

For each request, you get:

1. **Needs Analysis** — What packages you need and why
2. **Package Explanations** — What each tool does in simple terms
3. **Complete Setup Command** — One-liner to set everything up
4. **Requirements File** — Customized `requirements.txt` for your task
5. **Code Example** — Simple starter code for your specific use case
6. **Next Steps** — How to use it in VS Code or your editor

## Common Packages Explained

**Web Scraping Packages:**

- **requests** — Downloads web pages (like opening a URL in your browser)
- **beautifulsoup4** — Reads HTML and extracts data (like using Find & Replace)
- **selenium** — Automates a real browser (for JavaScript-heavy sites that need clicking)
- **lxml** — Fast HTML parser (similar to BeautifulSoup, but faster)

**Data Handling Packages:**

- **pandas** — Advanced data analysis and manipulation (for complex analysis)
- **csv** (built-in) — Simple CSV file writing (for basic needs, no install needed)
- **json** (built-in) — Save as JSON files (built into Python)
- **openpyxl** — Write to Excel files

**File & System Packages:**

- **os** (built-in) — File and folder management (built into Python)
- **pathlib** (built-in) — Modern file path handling (built into Python)
- **shutil** (built-in) — Copy and move files (built into Python)

**Other Useful Packages:**

- **python-dotenv** — Safe way to use passwords/API keys
- **schedule** — Schedule tasks to run at specific times
- **APScheduler** — Advanced task scheduling
- **smtplib** (built-in) — Send emails (built into Python)

## Package Decision Tree

```
Do you need to interact with JavaScript?
  → YES: Use Selenium
  → NO: Use requests + BeautifulSoup

Do you need to save data?
  → Simple CSV: Use built-in csv module
  → Complex analysis: Use pandas
  → Different format: Use json or openpyxl

Do you need to schedule it to run automatically?
  → YES: Use schedule or APScheduler
  → NO: Skip this
```

## Process

### 1. Describe Your Task

Tell me what you want to build. Be specific:
- Where are you scraping from?
- What data do you need?
- What do you do with the data (save, analyze, send)?
- Does the website need clicking or JavaScript interaction?

### 2. Get Analysis

I will:
- Identify what packages you need
- Explain why (in simple terms)
- Tell you what you DON'T need (and why)

### 3. Get Setup

You receive:
- Exact packages to install
- Customized `requirements.txt`
- ONE command to run
- Simple code example

### 4. Use In VS Code

Copy the setup command and run in your terminal (takes 1 minute).

---

## Example Flow

**You say:**
```
I want to scrape product prices from an Amazon search results page and save them to a CSV file
```

**I respond:**
```
You need:
✅ requests — to download the Amazon page
✅ beautifulsoup4 — to extract product prices
❌ selenium — NOT needed (Amazon doesn't require clicking)
❌ pandas — NOT needed (simple CSV is enough)

Setup command:
pip install requests beautifulsoup4

Code example:
[provide starter code]
```

---

## Benefits of This Skill

✅ **Beginner-friendly** — explains what each package does  
✅ **Customized** — no bloated requirements, only what you need  
✅ **Fast** — one command setup, not multiple installs  
✅ **Teaches you** — learn WHY you need each package  
✅ **Saves time** — no guessing, no trial-and-error  

---

## When to Use This Skill

Use `/python-setup` whenever you're starting a new Python project for:
- Web scraping
- Website automation
- Data extraction
- File processing
- Any Python task

---

## Next Steps After Setup

1. Run the setup command provided
2. Copy the starter code example
3. Modify it for your specific needs
4. Test it step by step

See `PYTHON_PROJECT_SETUP_GUIDE.md` for detailed virtual environment instructions.
