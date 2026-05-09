# Python Project Setup Guide - Quick Reference

**Use this guide every time you create a new Python project.** Save this file and refer back to it.

---

## Quick Setup (Copy-Paste for Every New Project)

```bash
# 1. Navigate to your project folder (created in VS Code)
cd path/to/your/project

# 2. Create virtual environment (one-time per project)
python3 -m venv venv

# 3. Activate virtual environment (do this every time you work on the project)
source venv/bin/activate

# 4. Upgrade pip (recommended, one-time)
pip install --upgrade pip

# 5. Install packages you need
pip install requests beautifulsoup4 matplotlib pandas

# 6. Save your packages to requirements.txt (for sharing/backup)
pip freeze > requirements.txt

# 7. Write and run your code
python your_script.py

# 8. Deactivate when done (optional)
deactivate
```

---

## Step-by-Step Explanation

### 1️⃣ Navigate to Your Project Folder
```bash
cd path/to/your/project
```
- Move into the project folder you created in VS Code
- Example: `cd ~/Documents/my-web-scraper`

### 2️⃣ Create Virtual Environment
```bash
python3 -m venv venv
```
- Creates an isolated sandbox called `venv`
- You'll see a new `venv/` folder appear in your project
- **You do this ONCE per project**
- This is the magic that prevents conflicts between projects

### 3️⃣ Activate Virtual Environment
```bash
source venv/bin/activate
```
- Activates the sandbox
- Your terminal prompt will change to show `(venv)` at the start
- Example: `(venv) your-computer:my-web-scraper you$`
- **You do this EVERY TIME you open the terminal and work on this project**
- This is important! If you forget, packages won't install in the right place

### 4️⃣ Install Packages
```bash
pip install requests beautifulsoup4
```
- Installs packages ONLY in this project's virtual environment
- Other projects on your Mac are NOT affected
- Each project has its own isolated packages

### 5️⃣ Create requirements.txt (For Backup/Sharing)
```bash
pip freeze > requirements.txt
```
- Saves all installed packages to a file
- If you share the project with someone or clone it later, they can do:
  ```bash
  pip install -r requirements.txt
  ```
- This installs all the same packages automatically

### 6️⃣ Run Your Code
```bash
python your_script.py
```
- Runs your Python script
- It automatically uses packages from the virtual environment
- Works because the virtual environment is activated

### 7️⃣ Deactivate (Optional)
```bash
deactivate
```
- Exits the virtual environment
- Only needed if you want to use system Python or another project
- Next time you work on this project, activate again with `source venv/bin/activate`

---

## Common Package Combinations for Different Tasks

### Web Scraping Project
```bash
pip install requests beautifulsoup4 selenium
```

### Data Analysis & Visualization Project
```bash
pip install pandas matplotlib seaborn numpy
```

### General Scripting & Utilities
```bash
pip install requests python-dotenv click
```

### All-in-One (If You're Not Sure)
```bash
pip install requests beautifulsoup4 pandas matplotlib seaborn numpy selenium
```

---

## Important: VS Code Configuration

When using Claude Code or VS Code:

1. **Select the correct Python interpreter:**
   - VS Code should show `./venv/bin/python` as an option
   - This tells VS Code to use your virtual environment

2. **Terminal auto-activation (Optional but helpful):**
   - VS Code can automatically activate `venv` when you open the terminal
   - No extra setup needed if you follow the guide above

---

## Workflow for Every New Project

```
1. Create project folder in VS Code
   ↓
2. Open terminal in VS Code
   ↓
3. Run: python3 -m venv venv
   ↓
4. Run: source venv/bin/activate
   ↓
5. Run: pip install [packages you need]
   ↓
6. Write your Python code
   ↓
7. Run your code with: python script.py
   ↓
8. When done: deactivate (optional)
```

That's it! Every project follows the same pattern.

---

## Troubleshooting

### ❌ "command not found: python3"
- Check: `which python3`
- Should show: `/usr/local/bin/python3`
- If not, your PATH might need fixing

### ❌ Virtual environment not activating
- Make sure you're in the project folder
- Run: `source venv/bin/activate`
- Look for `(venv)` at the start of your terminal prompt

### ❌ "pip: command not found" or packages not installing
- Make sure virtual environment is activated
- You should see `(venv)` in your prompt
- Run: `pip install package-name`

### ❌ "No module named X" when running code
- Make sure virtual environment is activated: `source venv/bin/activate`
- Make sure you installed the package: `pip install X`

### ❌ Need to use a different Python version for a specific project
- Create a new project folder
- Create a new virtual environment in that folder
- Virtual environments are project-specific and isolated

---

## What NOT to Do

❌ Don't install packages globally (without virtual environment)
- This is what caused your problems before

❌ Don't use system Python directly
- The official Python is for creating virtual environments

❌ Don't share virtual environments between projects
- Create a fresh `venv` for each project

✅ Do use virtual environments for every project
✅ Do save `requirements.txt` for sharing/backup
✅ Do activate virtual environment before installing packages

---

## Key Takeaway

```
ONE PROJECT = ONE FOLDER = ONE VIRTUAL ENVIRONMENT = NO CONFLICTS

Every new project is a clean slate with its own packages.
You never have to "install Python again" — just create a new venv folder.
```

---

## When Using Claude Code

If Claude Code creates or modifies your Python project, it will likely:
- Create the `venv` folder automatically
- Install packages in the virtual environment
- Run your code with the correct Python

Just remember to activate the virtual environment in your terminal when you want to run code manually:
```bash
source venv/bin/activate
```

---

**Bookmark this file. Refer back to the "Quick Setup" section every time you start a new Python project.**
