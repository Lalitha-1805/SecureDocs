# SecureDocs

SecureDocs is a Flask application for medical billing validation. It includes claim review workflows, PDF bill extraction, validation rules, anomaly detection, and role-based user accounts.

## Requirements

- Python 3.9 or later
- Poppler and Tesseract for PDF text extraction and OCR
- An approved medical billing dataset for dataset-dependent features

## Setup

Create and activate a virtual environment, then install the dependencies:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

Set a unique secret key for the Flask session. Keep it private and do not commit it:

```powershell
$env:SECRET_KEY = (python -c "import secrets; print(secrets.token_hex(32))")
```

Place an approved dataset at `data/medical_billing_dataset.csv` when using features that load the training dataset. The local dataset, database, uploaded bills, and session data are excluded from Git because they may contain sensitive information.

Install Poppler and Tesseract, then start the application:

```powershell
python run.py
```

Open http://127.0.0.1:5000 in a browser.

## Configuration and data

The application stores its SQLite database, uploaded documents, and filesystem sessions locally. Do not use real patient information in a development environment unless it is authorized and appropriately protected. Never commit `.env` files, credentials, databases, datasets, or uploaded documents.