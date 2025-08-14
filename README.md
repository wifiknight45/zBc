
 ### zBc_3.0v ie Postpaid Billing Date Calculator Script
---

### Summary
zBc – A lightweight yet powerful Python script designed to streamline key billing date calculations for post-paid wireless customers. By taking a single input date, zBc intelligently determines crucial billing milestones within the carrier's cycle, such as billing start dates, due dates, grace periods, and payment deadlines, ensuring users stay ahead of their financial obligation. For those who prioritize security, zBc offers AES-256 GCM encryption, providing a highly secure method to handle sensitive billing data without compromising performance. Built with simplicity and efficiency in mind, this script eliminates the guesswork in billing cycles while keeping operations smooth and automated. Whether you're a consumer looking for better billing clarity or an Account Associate aiming to optimize workflow, zBc is a reliable, low-footprint solution that gets the job done with minimal setup.

(v3.1‑beta)
An interactive Python tool for calculating key billing dates for postpaid wireless customers based on a user‑provided billing cycle start date (MM/DD/YYYY). Optionally supports AES‑256‑GCM encryption of billing data for secure storage or transmission.

This beta version has been adapted for interactive environments such as Jupyter Notebooks, Google Colab, or any compatible IDE.

Features
Billing date calculation: 
Automatically computes important dates such as:
Bill availability in app
Bill PDF readiness
Funds availability pre‑AutoPay
AutoPay draft date
Payment due date
Billing cycle close
Service suspension risk
Number loss risk

Date‑safe calculations: 
Correctly handles month/day rollovers.
Optional AES‑256‑GCM encryption of generated billing date data.

Notebook‑friendly logging for clear output in interactive environments.

Configurable password‑based key derivation using PBKDF2‑HMAC‑SHA256.

Requirements
Python: 3.7+

Libraries:
cryptography 

Install with:
bash
pip install cryptography

Installation
Clone this repository and install dependencies:

bash
git clone https://github.com/wifiknight45/zBc.git
cd <zBc>
pip install -r requirements.txt

Code
cryptography>=41.0.0
🛠 Usage
1. Import and run in Python
python
import datetime
from billing_calculator import calculate_billing_dates

start_date = datetime.date(2025, 6, 22)  # Example: Billing cycle start
dates = calculate_billing_dates(start_date)
print(dates)
2. Enable encryption
python
from billing_calculator import encrypt_billing_data

encrypted = encrypt_billing_data(dates, password="my_secure_password")
print(encrypted)

Example Output
python
{
  'billing_cycle_start': datetime.date(2025, 6, 22),
  'bill_in_tlife_app': datetime.date(2025, 6, 26),
  'bill_pdf_ready': datetime.date(2025, 7, 2),
  'funds_avail_pre_ap': datetime.date(2025, 7, 8),
  'autopay_draft': datetime.date(2025, 7, 10),
  'bill_is_due': datetime.date(2025, 7, 12),
  'billing_cycle_close': datetime.date(2025, 7, 22),
  'service_suspension_risk': datetime.date(2025, 7, 29),
  'number_loss_risk': datetime.date(2025, 9, 20)
}

Security Notes
Uses PBKDF2‑HMAC‑SHA256 for password‑based AES‑256 key derivation.
Uses 12‑byte nonce for AES‑GCM encryption (recommended size).
Always store salts, nonces, and ciphertext securely; never reuse nonces for the same key.

🧪 Testing
You can quickly test the calculator and encryption in an interactive session (Jupyter/Colab) or standard Python REPL.
