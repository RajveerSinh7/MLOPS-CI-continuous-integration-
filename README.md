# 🧠 Streamlit CI/CD Demo

This project demonstrates an **end-to-end Continuous Integration (CI)** pipeline using **GitHub Actions** for a simple Python app built with **Streamlit**.

---

## 🚀 Project Overview

The goal of this project is to automate testing every time new code is pushed or a pull request is created.  
GitHub Actions runs automatically to:
- Install dependencies  
- Run tests  
- Ensure code quality and functionality  

---

## 🗂️ Project Structure

```
Streamlit-CI-Demo/
│
├── app.py                 # Simple Streamlit app
├── test_app.py            # Test script for CI
├── requirements.txt       # Dependencies
├── README.md              # Project documentation
│
└── .github/
    └── workflows/
        └── ci.yml         # GitHub Actions workflow file
```

---

## ⚙️ Step-by-Step Setup

### 1️⃣ Create a Simple Streamlit App

**app.py**
```python
import streamlit as st

st.title("Hello Streamlit!")
st.write("This is a simple Streamlit app to demonstrate CI/CD with GitHub Actions.")
```

---

### 2️⃣ Create a Virtual Environment (optional but recommended)

```bash
python3 -m venv venv
source venv/bin/activate   # For Mac/Linux
venv\Scripts\activate      # For Windows
```

Then install dependencies:

```bash
pip install streamlit pytest
pip freeze > requirements.txt
```

---

### 3️⃣ Create the GitHub Actions Workflow

Create folders:

```bash
mkdir -p .github/workflows
```

Then inside `.github/workflows/`, create a file named `ci.yml`.

**.github/workflows/ci.yml**
```yaml
name: Streamlit CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.12'

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run tests
        run: pytest
```

---

### 4️⃣ Write a Simple Test Script

**test_app.py**
```python
import pytest

def test_streamlit_runs():
    assert True  # Dummy test to ensure CI passes

def test_sum():
    assert 2 + 2 == 4
```

---

### 5️⃣ Push Everything to GitHub

```bash
git init
git add .
git commit -m "Initial commit with CI workflow"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

---

### 6️⃣ Check CI Pipeline on GitHub

1. Go to your repository on GitHub.  
2. Click on the **“Actions”** tab.  
3. You’ll see your workflow running under “Streamlit CI”.  
4. ✅ If all tests pass, the CI pipeline is successful!

---

## 🧩 Optional Enhancements

- Add **flake8** for linting (`pip install flake8`)  
- Add **Streamlit deployment** to Streamlit Cloud or AWS in CI/CD  
- Add test coverage reports  

---

## 👨‍💻 Author

**Rajveer Jadav**  
📧 r2jadav@uwaterloo.ca  
🔗 [LinkedIn](https://linkedin.com/in/rajveer-sinh-jadav-414971166/) | [GitHub](https://github.com/RajveerSinh7)

---

## 🏁 License

This project is licensed under the MIT License — see the LICENSE file for details.

