# Project Environment Setup Guide

This document explains how to correctly set up the Python environment for this project using a **local virtual environment** (`.venv`). Following these steps ensures everyone has the **same libraries, same versions, and the same notebook execution environment**, regardless of operating system.

***

## Step 1. Navigate to the Project Folder

Open VS Code, then open the folder containing the project.

Next, open a terminal (VS Code → Terminal → New Terminal) and make sure you are inside the project directory:

***

## 2. Create the Virtual Environment

#### macOS / Linux:
```bash
python3 -m venv .venv
```

#### Windows:
```bash
python -m venv .venv
```

This creates a hidden folder named `.venv` inside the project.
Each team member has their own `.venv` — **it is not shared or committed to GitHub because it is too large**, similar to how we did with the dataset.

***

## 3. Activate the Virtual Environment

#### macOS / Linux:
```bash
source .venv/bin/activate
```

#### Windows PowerShell:
```bash
.venv\Scripts\Activate.ps1
```

#### Windows CMD:
```bash
.venv\Scripts\activate.bat
```


You should now see (.venv) in your terminal prompt.

```bash
(.venv) user@computer:~/path/to/project
```

If not, **STOP** — the environment is not activated correctly.

***

## 4. Install the Required Packages

With the venv activated, run:
```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

This installs all dependencies (numpy, pandas, matplotlib, scikit-learn, tensorflow, etc.) inside the venv only.

***

## 5. Restart VS Code (IMPORTANT)

Before selecting the interpreter in VS Code,
close and reopen the entire VS Code application.

If you don’t do this, the newly created .venv may not appear in the interpreter list.

***

## 6. Select the Correct Python Interpreter in VS Code

After reopening VS Code:
1. Press **Ctrl + Shift + P** (Cmd + Shift + P on Mac)
2. Choose: **Python: Select Interpreter**
3. Pick the one located in:

#### macOS / Linux:
```bash
<project-folder>/.venv/bin/python
```

#### Windows:
```bash
<project-folder>\.venv\Scripts\python.exe
```

This tells VS Code to use the virtual environment for **all Python execution**.

If you see multiple interpreters, choose the one **inside the project’s `.venv` folder** only.

***

## 7. Select the Correct Kernel for Jupyter Notebooks

Whenever you open a Jupyter notebook in VS Code:
1. Click the kernel name at the top right
2. Choose the interpreter from:

#### macOS / Linux:
```bash
<project-folder>/.venv/bin/python
```

#### Windows:
```bash
<project-folder>\.venv\Scripts\python.exe
```

This ensures the notebook runs with the same environment you installed packages into.

***

## 8. Validate the Setup

Inside the notebook, run the first cell to try and import the packages

If you see "Setup OK" and no errors → setup is correct.

***

## 9. Troubleshooting

#### ❌ “ModuleNotFoundError” even after installing packages

The notebook is probably using the wrong kernel.
Select the .venv interpreter again (Step 7).

#### ❌ The .venv folder does not appear in VS Code interpreter list

You did may have not restarted VS Code — do Step 5.

#### ❌ Terminal shows both (.venv) and (base)

Conda is auto-activating. Disable it:

```bash
conda config --set auto_activate_base false
```

Restart the terminal, then activate `.venv` again.

#### ❌ Pip installs packages but they don’t show up

Always use:

```bash
python -m pip install ...
```

to ensure pip installs into the active environment.

***

## 10. Important Notes

- Never commit your `.venv` folder. It should stay local. It is already listed in .gitignore.

- The environment can always be rebuilt using:
```bash
python -m venv .venv
python -m pip install -r requirements.txt
```

All team members will have identical environments as long as
requirements.txt stays updated.

***

## 🎉 Done!

Once everyone completes this setup, all notebooks, scripts, and imports will run consistently across machines.

If anything breaks, re-activate the venv and re-select the interpreter — those two steps fix 95% of issues.