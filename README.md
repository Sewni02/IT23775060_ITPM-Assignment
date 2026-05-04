# Singlish Chat Translator – Test Automation README

## Project Overview
This project automates the testing of the Singlish-to-Sinhala chat translator available at:
**https://www.pixelssuite.com/chat-translator**

The automation script inputs Singlish text, captures the translation output, and compares it against expected Sinhala translations recorded in an Excel file.

---

## Folder Structure
```
IT23775060_ITPM-Assignment-main
│
├── IT23775060.py          # Main Playwright automation script
├── IT23775060.xlsx  # Test case data file
└── README.md                # Quick reference commands
```

---

## Prerequisites (One-Time Setup)

### 1. Install Python
- Download and install **Python 3.11 or 3.12** from https://www.python.org/downloads/
- During installation, check **"Add Python to PATH"**

### 2. Install Google Chrome
- Download from https://www.google.com/chrome/
- *(Optional — Playwright can install Chromium automatically)*

---

## Setup Instructions

### Step 1 – Extract the Project
- Extract it → folder should be: `IT23775060_ITPM-Assignment-main`

### Step 2 – Open Command Prompt
- Press `Win + R` → type `cmd` → press Enter

### Step 3 – Navigate to Project Folder
```
IT23775060_ITPM-Assignment-main
```

### Step 4 – Install Dependencies (One-Time)
Run these commands one by one:
```
pip install -U pip
pip install playwright openpyxl
playwright install
```

---

## How to Add Test Cases

Open **Assignment 1 - Test cases.xlsx** and fill in these columns:

| Column | Header | Description |
|--------|--------|-------------|
| A | TC ID | Unique test case ID (e.g. Pos_001, Neg_001) |
| B | Input length type | S = Short (≤30), M = Medium (31–299), L = Long (300+) |
| C | Input | Singlish text to be translated |
| D | Expected output | Expected Sinhala translation |
| E | Actual output |  Leave blank — auto-filled by script |
| F | Status |  Leave blank — auto-filled by script |
| G | Singlish input types covered | Input categories (e.g. compound sentence, slang) |
| H | Evidence or rationale | Why this input type is covered |

>  **Do NOT enter values in columns E and F** — the script fills these automatically.

#### Typing multiple lines in one cell (Excel tip)
Press **Alt + Enter** inside a cell to go to a new line.
Make sure **Wrap Text** is ON: Home → Wrap Text

---

## How to Run the Script

From `IT23775060_ITPM-Assignment-main` in Command Prompt, run:

```
python IT23775060.py --excel "IT23775060.xlsx" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 5000 --type-delay-ms 80 --slow-mo-ms 200 --save-every 1 --keep-open
```

### Command Arguments Explained

| Argument | Value | Description |
|----------|-------|-------------|
| `--excel` | file path | Path to the Excel test cases file |
| `--url` | URL | Target translator website |
| `--wait-ms` | 5000 | Wait time (ms) after each input |
| `--type-delay-ms` | 80 | Delay between keystrokes (ms) |
| `--slow-mo-ms` | 200 | Slow motion delay for browser actions |
| `--save-every` | 1 | Save Excel after every N test cases |
| `--keep-open` | — | Keep browser open after test completes |

---

## Checking Results

1. After the script finishes, go to `IT23775060_ITPM-Assignment-main`
2. Reopen **Assignment 1 - Test cases.xlsx**
3. Check columns **E (Actual output)** and **F (Status)**
   - **Pass** = Actual output matches Expected output
   -  **Fail** = Mismatch detected

---

## Test Case Types Reference

| Input Type | Description |
|------------|-------------|
| Simple/interrogative | Basic question sentences |
| Compound/complex | Multi-clause sentences |
| Mixed Singlish + English | Code-switching inputs |
| Slang/colloquial | Informal expressions |
| Imperative/command | Action commands |
| Negation patterns | Sentences with negation |
| Tense variations | Past / present / future |
| Measurement units | km, kg, mm, RS etc. |
| English abbreviations | NIC, ATM, BBQ, SMS etc. |
| Time/date formats | 7AM, 2PM, 2026-07-15 etc. |
| Greeting sentences | Formal/informal greetings |

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| `pip` not recognized | Reinstall Python with "Add to PATH" checked |
| Browser doesn't open | Run `playwright install` again |
| Script stops mid-way | Check internet connection; re-run script |
| Excel not updating | Make sure the file is closed before running |

---

## Contact
For issues related to the test script or Excel file, refer to your assignment document or contact your supervisor.
