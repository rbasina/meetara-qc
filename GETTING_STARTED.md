# Getting Started

Use this guide to set up your local environment and run the course in the intended order.

## 1. Prerequisites
1. Python 3.10 or 3.11
2. Git
3. A standard laptop (8 GB RAM is enough for beginner and most intermediate labs)

## 2. Clone Repository

```powershell
git clone https://github.com/rbasina/meeTARA-qc.git
cd meeTARA-qc
```

## 3. Create and Activate Virtual Environment

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
```

## 4. Install Core Packages

```powershell
pip install -r requirements.txt
```

Optional for hardware chapters:

```powershell
pip install qiskit-ibm-runtime
```

## 5. Launch Notebooks

```powershell
jupyter notebook
```

## 6. Recommended Learning Order
1. Read CHAPTER_00 first.
2. Complete beginner notebooks 01 to 04.
3. Complete intermediate notebooks 05 to 08.
4. Complete advanced notebooks 09 to 12.

## 7. Execution Policy
1. Use simulator-first workflow by default.
2. Keep shot counts controlled (start with 1024).
3. Use repeated runs for decisions.
4. Record pass or investigate thresholds before running experiments.

## 8. Troubleshooting
1. If imports fail, confirm virtual environment is active.
2. If notebook kernel is missing, select the Python interpreter from .venv.
3. If plots do not render, run notebook cells in order from top to bottom.