# Python Setup Skill - Usage Examples

Real-world examples of how to use the Python setup skill.

---

## Example 1: Simple Web Scraper

### Your Task:
```
I want to scrape product names and prices from an e-commerce website and save them to a CSV file.
```

### Analysis Response:

**What you need:**
- ✅ **requests** — downloads the web page
- ✅ **beautifulsoup4** — extracts product data
- ❌ **selenium** — NOT needed (no clicking required)
- ❌ **pandas** — NOT needed (simple CSV is enough)

**Setup Command:**
```bash
cd your-project-folder
python3 -m venv venv
source venv/bin/activate
pip install requests beautifulsoup4
```

**Starter Code:**
```python
import requests
from bs4 import BeautifulSoup
import csv

# Download the page
url = "https://example-store.com/products"
response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')

# Extract product data
products = []
for item in soup.find_all('div', class_='product'):
    name = item.find('h2').text
    price = item.find('span', class_='price').text
    products.append({'name': name, 'price': price})

# Save to CSV
with open('products.csv', 'w') as f:
    writer = csv.DictWriter(f, fieldnames=['name', 'price'])
    writer.writeheader()
    writer.writerows(products)

print(f"Saved {len(products)} products to products.csv")
```

---

## Example 2: JavaScript-Heavy Website Scraping

### Your Task:
```
I need to scrape data from a website that loads content when I click "Load More" button. After scrolling, I need to save all the data to a CSV.
```

### Analysis Response:

**What you need:**
- ✅ **selenium** — automates browser clicking
- ✅ **beautifulsoup4** — extracts data
- ✅ **requests** — not directly needed, but good to have
- ❌ **pandas** — NOT needed (simple CSV is enough)

**Setup Command:**
```bash
cd your-project-folder
python3 -m venv venv
source venv/bin/activate
pip install selenium beautifulsoup4
```

**Starter Code:**
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from bs4 import BeautifulSoup
import csv
import time

# Start browser
driver = webdriver.Chrome()
driver.get("https://example.com")

# Click "Load More" multiple times
for i in range(5):
    try:
        load_btn = driver.find_element(By.CLASS_NAME, 'load-more')
        load_btn.click()
        time.sleep(2)  # Wait for content to load
    except:
        print("No more items to load")
        break

# Extract data
soup = BeautifulSoup(driver.page_source, 'html.parser')
items = []
for item in soup.find_all('div', class_='item'):
    items.append({'data': item.text})

# Save to CSV
with open('items.csv', 'w') as f:
    writer = csv.DictWriter(f, fieldnames=['data'])
    writer.writeheader()
    writer.writerows(items)

driver.quit()
print(f"Saved {len(items)} items to items.csv")
```

---

## Example 3: Data Analysis & Visualization

### Your Task:
```
I want to scrape stock prices from a financial website over multiple days and create charts to analyze the trends.
```

### Analysis Response:

**What you need:**
- ✅ **requests** — downloads web pages
- ✅ **beautifulsoup4** — extracts stock data
- ✅ **pandas** — analyze price trends
- ✅ **matplotlib** — create charts
- ❌ **selenium** — NOT needed (no JavaScript)

**Setup Command:**
```bash
cd your-project-folder
python3 -m venv venv
source venv/bin/activate
pip install requests beautifulsoup4 pandas matplotlib
```

**Starter Code:**
```python
import requests
from bs4 import BeautifulSoup
import pandas as pd
import matplotlib.pyplot as plt

# Scrape stock data
url = "https://example-stocks.com/prices"
response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')

# Extract and organize data
prices = []
for row in soup.find_all('tr')[1:]:  # Skip header
    cols = row.find_all('td')
    date = cols[0].text
    price = float(cols[1].text)
    prices.append({'date': date, 'price': price})

# Convert to DataFrame
df = pd.DataFrame(prices)
df['date'] = pd.to_datetime(df['date'])
df = df.sort_values('date')

# Create chart
plt.figure(figsize=(10, 6))
plt.plot(df['date'], df['price'], marker='o')
plt.title('Stock Price Trend')
plt.xlabel('Date')
plt.ylabel('Price ($)')
plt.xticks(rotation=45)
plt.tight_layout()
plt.savefig('price_trend.png')
print("Chart saved as price_trend.png")

# Statistics
print(f"Average Price: ${df['price'].mean():.2f}")
print(f"Min Price: ${df['price'].min():.2f}")
print(f"Max Price: ${df['price'].max():.2f}")
```

---

## Example 4: Image Downloader

### Your Task:
```
I want to download all images from a Pinterest board and save them organized by category folders.
```

### Analysis Response:

**What you need:**
- ✅ **requests** — downloads images
- ✅ **beautifulsoup4** — finds image URLs
- ❌ **selenium** — NOT needed (can use requests)
- ❌ **pandas** — NOT needed (no data analysis)

**Setup Command:**
```bash
cd your-project-folder
python3 -m venv venv
source venv/bin/activate
pip install requests beautifulsoup4
```

**Starter Code:**
```python
import requests
from bs4 import BeautifulSoup
import os

# Create folders for categories
categories = ['nature', 'design', 'photography']
for cat in categories:
    os.makedirs(f'images/{cat}', exist_ok=True)

# Download images
url = "https://example.com/images"
response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')

count = 0
for img in soup.find_all('img'):
    img_url = img.get('src')
    category = img.get('data-category', 'uncategorized')
    
    img_data = requests.get(img_url).content
    filename = f'images/{category}/image_{count}.jpg'
    
    with open(filename, 'wb') as f:
        f.write(img_data)
    
    count += 1
    print(f"Downloaded {count} images")

print(f"Total images downloaded: {count}")
```

---

## Example 5: Price Monitoring & Alerts

### Your Task:
```
I want to monitor a product price on an e-commerce site and send myself an email alert if the price drops below a certain amount.
```

### Analysis Response:

**What you need:**
- ✅ **requests** — downloads product page
- ✅ **beautifulsoup4** — extracts price
- ❌ **selenium** — NOT needed (no clicking)
- ❌ **pandas** — NOT needed (simple logic)

**Setup Command:**
```bash
cd your-project-folder
python3 -m venv venv
source venv/bin/activate
pip install requests beautifulsoup4 python-dotenv
```

**Starter Code:**
```python
import requests
from bs4 import BeautifulSoup
import smtplib
from email.mime.text import MIMEText
import os
from dotenv import load_dotenv

load_dotenv()

# Configuration
TARGET_PRICE = 50.00
PRODUCT_URL = "https://example.com/product/12345"
EMAIL = os.getenv('EMAIL')
PASSWORD = os.getenv('EMAIL_PASSWORD')

# Check price
response = requests.get(PRODUCT_URL)
soup = BeautifulSoup(response.content, 'html.parser')
current_price = float(soup.find('span', class_='price').text.replace('$', ''))

print(f"Current price: ${current_price}")

# Send alert if price is low
if current_price < TARGET_PRICE:
    # Send email
    msg = MIMEText(f"Price dropped to ${current_price}!")
    msg['Subject'] = 'Price Alert!'
    msg['From'] = EMAIL
    msg['To'] = EMAIL
    
    with smtplib.SMTP_SSL('smtp.gmail.com', 465) as server:
        server.login(EMAIL, PASSWORD)
        server.send_message(msg)
    
    print(f"Alert sent! Price is below ${TARGET_PRICE}")
else:
    print(f"Price is still above ${TARGET_PRICE}")
```

---

## Quick Reference: Which Packages Do I Need?

| Task | packages |
|------|----------|
| Simple web scraping | `requests beautifulsoup4` |
| JavaScript-heavy site | `selenium beautifulsoup4` |
| Data analysis | `pandas matplotlib` |
| Image downloading | `requests` |
| CSV saving | Built-in `csv` (no install needed) |
| Scheduled tasks | `schedule` or `APScheduler` |
| Email alerts | Built-in `smtplib` (no install needed) |
| Safe credentials | `python-dotenv` |

---

## Key Rules to Remember

1. **Don't over-install** — Only install what you actually need
2. **Read errors** — Python errors tell you exactly what's wrong
3. **Test step-by-step** — Write and test one part at a time
4. **Use virtual environments** — Always! (See PYTHON_PROJECT_SETUP_GUIDE.md)
5. **Save requirements.txt** — For sharing your project with others

---

## Next Steps

1. Describe your Python task (what you want to build)
2. Get the analysis (what packages you need)
3. Run the setup command
4. Copy the starter code
5. Modify it for your needs
6. Test it!

Happy coding! 🐍
