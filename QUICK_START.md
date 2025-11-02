# FraudGuard - Quick Start Guide

## Setup in 5 Minutes ⚡

### Step 1: Install Dependencies

```powershell
# In project directory
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

### Step 2: Set Gemini API Key (Optional)

Get your free API key from: https://makersuite.google.com/app/apikey

```powershell
$env:GEMINI_API_KEY="your-api-key-here"
```

Or edit `config.py` and set:
```python
GEMINI_API_KEY = 'your-api-key-here'
```

### Step 3: Run the Application

```powershell
python app.py
```

Navigate to: **http://127.0.0.1:5000**

### Step 4: Create Account & Explore

1. **Register**: Click "Register" and create an account
2. **Login**: Use your username and password
3. **Dashboard**: Explore your ₹10,000 balance
4. **Enable 2FA** (optional): Click "Set up now" notification
5. **Try Features**:
   - Send money to another user
   - Run fraud detection simulations
   - View API documentation
   - Read user guide

## Testing the System

### Create Test Users

Register at least 2 accounts to test money transfers:
- Username: alice, Password: testpass123
- Username: bob, Password: testpass123

### Test Transaction Flow

1. Login as **alice**
2. Click "Send Money" on dashboard
3. Recipient: **bob**
4. Amount: Try ₹500 (normal) then ₹5000 (triggers fraud check)
5. Check "Face verification" checkbox
6. Submit

### Test Fraud Detection

1. Go to **Simulations** page
2. Select **Email** data type
3. Try this phishing example:
```
URGENT: Your account has been suspended!
Click here immediately to verify:
http://suspicious-link.com/verify
```
4. Click "Run Simulation"
5. View fraud score and indicators

### Test 2FA Setup

1. Dashboard → Click "Set up now" for 2FA
2. Install Google Authenticator on phone
3. Scan QR code
4. Enter 6-digit code
5. Logout and login again with 2FA code

## Features Checklist

- [x] **Login/Registration**: Username normalization, password hashing
- [x] **2FA**: Google Authenticator with QR code
- [x] **Dummy Money**: ₹10,000 starting balance
- [x] **Transactions**: P2P money transfers
- [x] **Fraud Detection**: AI analysis for large transactions
- [x] **Face Verification**: Checkbox confirmation (demo)
- [x] **Dashboard**: Balance, transactions, insights
- [x] **Simulations**: Test fraud detection with chat logs
- [x] **API Endpoints**: RESTful fraud check, auth, tokenization
- [x] **Documentation**: API docs, user guide, FAQ
- [x] **Contact Form**: Support requests
- [x] **Responsive Design**: Mobile-friendly Bootstrap layout

## Common Tasks

### Send Money
Dashboard → Send Money button → Fill form → Check face verification → Submit

### View Transactions
Dashboard → Recent Transactions panel → See sent/received payments

### Approve Flagged Transaction
Dashboard → Flagged Activities → Approve or Cancel button

### Run Fraud Simulation
Simulations → Select data type → Enter content → Run Simulation

### Generate API Token
Use `/api/auth/token` endpoint with username/password

### Check API Documentation
Navigate to API Docs page → Browse endpoints

## Troubleshooting

**Can't login?**
- Check username is correct (case-insensitive)
- If 2FA enabled, enter 6-digit code
- Ensure password is correct

**Transaction failed?**
- Check sufficient balance
- Verify recipient username exists
- Must check face verification box

**Gemini API errors?**
- Set GEMINI_API_KEY in config.py or environment
- Check internet connection
- Verify API key is valid

**Database errors?**
- Delete `app.db` and restart
- Run `python app.py` to recreate

## Default Configuration

- **Initial Balance**: ₹10,000
- **Large Transaction Threshold**: 30% of balance
- **Fraud Score Threshold**: 0.7 (flagged if exceeded)
- **Database**: SQLite (app.db)
- **Debug Mode**: Enabled (disable in production)

## Next Steps

1. **Customize**: Edit `config.py` for your settings
2. **Secure**: Change SECRET_KEY to random value
3. **Test**: Create multiple users, try all features
4. **Integrate**: Use API endpoints in your apps
5. **Learn**: Read user guide for integration details

## Support

Need help? Check:
- `/user-guide` - Full integration guide
- `/faq` - Common questions
- `/contact` - Send support request
- `README_FRAUDGUARD.md` - Complete documentation

---

**Ready to explore FraudGuard!** 🚀
