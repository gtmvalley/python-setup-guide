# Python Project Setup Guide

A comprehensive guide for setting up Python projects with virtual environments on macOS.

## Overview

This repository contains a complete guide for setting up Python projects using virtual environments. It solves the common problem of package conflicts between projects and eliminates the need to reinstall dependencies repeatedly.

## Contents

- **PYTHON_PROJECT_SETUP_GUIDE.md** - Complete step-by-step guide with examples and troubleshooting

## Quick Start

1. Clone this repository or copy the guide
2. Create a new Python project folder
3. Follow the guide in `PYTHON_PROJECT_SETUP_GUIDE.md`
4. Reference the "Quick Setup" section for every new project

## What You'll Learn

- ✅ Setting up virtual environments with `venv`
- ✅ Installing packages locally (no conflicts)
- ✅ Managing dependencies with `requirements.txt`
- ✅ Activating and deactivating virtual environments
- ✅ Troubleshooting common issues
- ✅ Best practices for Python project structure

## The Problem This Solves

Before using virtual environments:
- ❌ Installing packages globally creates conflicts
- ❌ Different projects need different package versions
- ❌ New projects inherit dependencies from old projects
- ❌ Repeated setup for every new project

After using virtual environments:
- ✅ Each project has isolated dependencies
- ✅ No conflicts between projects
- ✅ Clean, fresh start for each project
- ✅ Reproducible setup with `requirements.txt`

## Key Principle

```
ONE PROJECT = ONE FOLDER = ONE VIRTUAL ENVIRONMENT = NO CONFLICTS
```

## Prerequisites

- Python 3.x installed (official Python from python.org)
- Basic terminal knowledge
- A code editor (VS Code, PyCharm, etc.)

## Usage

For a quick reference, jump to the **"Quick Setup"** section in `PYTHON_PROJECT_SETUP_GUIDE.md`:

```bash
# Every new project, run these commands:
cd path/to/your/project
python3 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install [your-packages]
```

## Who Is This For?

- Beginners starting Python development
- Developers setting up multiple Python projects
- Anyone tired of package conflicts and repeated installations
- Teams collaborating on Python projects

## Additional Resources

- [Official Python Documentation](https://docs.python.org)
- [Virtual Environments - Python.org](https://docs.python.org/3/tutorial/venv.html)
- [pip Documentation](https://pip.pypa.io/)

## File Structure

```
python-setup-guide/
├── README.md
├── PYTHON_PROJECT_SETUP_GUIDE.md
└── .gitignore
```

## Contributing

This is a personal reference guide. Feel free to fork and customize for your needs.

## License

MIT - Feel free to use this guide for any purpose.

---

**Last Updated:** 2026-05-09  
**Python Version:** 3.14.4+
