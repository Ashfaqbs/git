# **Python Project – GitHub CLI Workflow**

This document provides a reusable reference for publishing a simple Python project to GitHub entirely through the command line.
It covers initializing Git, committing code, creating a GitHub repo via the GitHub CLI, and pushing the project online.

The sample repository name used in this guide:

**`python-starter-demo`**

---

## **1. Navigate to  Python project directory**

```bash
cd path/to/your/python/project
```

Example:

```bash
cd ~/projects/my-python-app
```

This directory might contain files like:

```
main.py
requirements.txt
utils/
README.md
```

---

## **2. Initialize Git for the project**

```bash
git init
```

This sets up version control in Python project folder.

---

## **3. Add all project files to Git**

```bash
git add .
```

This stages everything — the `.py` files, modules, and configs.

---

## **4. Commit the staged files**

```bash
git commit -m "Initial commit: simple python project"
```

This creates the first snapshot of the code.

---

## **5. Create a GitHub repository using GitHub CLI**

```bash
gh repo create python-starter-demo --public --source=. --remote=origin
```

Private version:

```bash
gh repo create python-starter-demo --private --source=. --remote=origin
```

This command:

* Creates a new repo on GitHub
* Links it to the local directory as `origin`
* Does **not** open a browser
* Keeps everything inside the CLI

---

## **6. Push the project to GitHub**

```bash
git push -u origin main
```

(If the default branch is `master`, use `master` instead of `main`.)

---

## **7. Verify the remote repository**

```bash
git remote -v
```

Expected output:

```
origin  https://github.com/<your-username>/python-starter-demo.git (fetch)
origin  https://github.com/<your-username>/python-starter-demo.git (push)
```

---

## **Copy-Paste Ready Summary**

```bash
cd project-folder
git init
git add .
git commit -m "Initial commit: simple python project"
gh repo create python-starter-demo --public --source=. --remote=origin
git push -u origin main
```

---
