# 🛡️ FraudGuard - AI-Powered Fraud Detection Platform# Flask Authentication Starter



A comprehensive, production-ready fraud detection platform built with Flask, featuring AI-powered analysis via Google's Gemini API, real-time transaction monitoring, biometric authentication, and an intuitive dashboard for fraud prevention and analysis.A clean, secure Flask application with user authentication featuring:



## ✨ Features



## 📋 Table of Contents- **Secure Authentication**: Registration and login with Werkzeug password hashing

- **Username Normalization**: Usernames are lowercase and case-insensitive

1. [Overview](#overview)- **Strong Validation**: 

2. [Core Features](#core-features)  - Username: 3-20 chars, alphanumeric + underscore only

3. [Technology Stack](#technology-stack)  - Email: Valid email format required

4. [Installation](#installation)  - Password: Minimum 8 characters

5. [Configuration](#configuration)- **Responsive Design**: Bootstrap 5 navbar layout works on all devices

6. [Project Structure](#project-structure)- **Flash Messages**: User-friendly feedback for all actions

7. [Database Models](#database-models)- **Protected Routes**: Dashboard only accessible when logged in

8. [API Endpoints](#api-endpoints)- **Session Management**: Flask-Login handles user sessions securely

9. [User Features](#user-features)

10. [Developer Guide](#developer-guide)## 🚀 Quick Start (Windows PowerShell)

11. [Troubleshooting](#troubleshooting)

12. [Contributing](#contributing)```powershell

# Create virtual environment

---python -m venv .venv



## 🎯 Overview# Activate virtual environment

.\.venv\Scripts\Activate.ps1

**FraudGuard** is an enterprise-grade fraud detection system designed to:

# Install dependencies

- ✅ **Detect fraudulent transactions** using AI and machine learningpip install -U pip

- ✅ **Monitor multiple data types**: emails, SMS, phone numbers, and transactionspip install -r requirements.txt

- ✅ **Provide real-time alerts** for suspicious activities

- ✅ **Enable secure authentication** with 2FA and biometric verification# Run the application

- ✅ **Generate actionable insights** through interactive dashboardspython app.py

- ✅ **Support API integration** for third-party applications```

- ✅ **Offer compliance tools** for enterprise customers

Navigate to: **http://127.0.0.1:5000**

---

## 📁 Project Structure

## 🌟 Core Features



### 🔐 **Authentication & Security**├── app.py              # Main application (models, forms, routes)

├── requirements.txt    # Python dependencies

#### Two-Factor Authentication (2FA)├── templates/          # HTML templates (Jinja2)

- **Google Authenticator Integration**: QR code-based TOTP setup│   ├── base.html       # Base layout with navbar

- **Time-based One-Time Passwords**: Secure 6-digit codes│   ├── index.html      # Homepage

- **Recovery Codes**: Store safely for account recovery│   ├── login.html      # Login form

- **Status Page**: Enable/disable 2FA anytime from account settings│   ├── register.html   # Registration form

- **Auto-logout**: Sessions expire after 1 hour of inactivity│   └── dashboard.html  # Protected user dashboard

└── static/

#### Biometric Face Verification    └── styles.css      # Custom CSS

- **Webcam Integration**: Real-time face detection```

- **Modal-based Capture**: Beautiful UX with camera preview

- **Success Feedback**: Button transforms to green checkmark ✓## 🔒 Security Notes

- **Demo Mode**: Auto-verifies for testing without webcam

- **Transaction Requirement**: Optional for additional security- **SECRET_KEY**: Change `app.config['SECRET_KEY']` to a secure random value in production

- **Database**: Uses SQLite (`app.db`) for development. Switch to PostgreSQL/MySQL for production

#### Username Normalization- **HTTPS**: Always use HTTPS in production to protect credentials in transit

- Case-insensitive usernames- **Password Hashing**: Werkzeug's `generate_password_hash()` uses secure defaults

- Unique email addresses per account

- Password hashing with Werkzeug security## 📝 User Restrictions



---- **Username**: 3-20 characters, letters/numbers/underscore only, automatically lowercased

- **Email**: Must be valid email format, unique

### 💰 **Transaction System**- **Password**: Minimum 8 characters (no maximum for security)

- All usernames and emails are case-insensitive for consistency

#### Peer-to-Peer Money Transfers

- **Dummy Money Balance**: Every user starts with ₹10,000## 🎨 Responsive Layout

- **Send Money Modal**: Quick, intuitive interface

- **Real-time Balance Updates**: Instant debit/creditThe Bootstrap 5 navbar automatically adapts:

- **Transaction History**: All transactions tracked with timestamps- **Desktop**: Horizontal menu

- **Recipient Validation**: Prevents self-transfers and invalid recipients- **Mobile**: Collapsible hamburger menu

- **Tablet**: Optimized for medium screens

#### Fraud Detection on Transactions
- **Large Transaction Threshold**: 30% of balance triggers AI check
- **Real-time Gemini Analysis**: Analyzes transaction context
- **Fraud Score**: 0-1 confidence rating
- **Auto-flagging**: High-risk transactions held for review
- **Manual Approval**: Users can approve flagged transactions

#### Transaction Status Tracking
- **Pending**: Awaiting fraud check completion
- **Completed**: Successfully transferred
- **Flagged**: Held for review (fraud score > 0.7)
- **Cancelled**: Rejected or user-cancelled

---

### 🤖 **AI-Powered Fraud Detection (Gemini Integration)**

#### Supported Data Types

**Email Fraud Detection**
- Phishing attempts
- Suspicious attachments/links
- Social engineering tactics
- Impersonation of trusted entities

**SMS Fraud Detection (Smishing)**
- Prize/lottery scams
- Urgent action requests
- Account verification requests
- Malicious shortened URLs

**Phone Number Analysis**
- Known scam database matches
- VoIP provider detection
- Geographic anomalies
- Spoofing indicators

**Transaction Analysis**
- Unusual amounts (structuring patterns)
- Suspicious receiver accounts
- Rapid succession of transfers
- High-risk jurisdictions
- Account takeover signs

#### Gemini API Configuration
- **Current Model**: `gemini-2.0-flash-exp` (latest, with fallbacks)
- **Fallback Chain**: 2.0 Flash → 1.5 Flash → 1.5 Pro
- **Response Format**: Structured JSON with confidence scores
- **Error Handling**: Full stack trace logging for debugging

---

### 📊 **Dashboard & Analytics**

**Balance Overview Card**
- Current ₹ balance in large, clear font
- Real-time updates after transactions

**Financial Insights Panel**
- Total Received: Sum of all incoming transfers
- Total Sent: Sum of all outgoing transfers
- Transaction Count: Total transactions performed
- Fraud Checks Passed: Successfully completed transactions

**Recent Transactions List**
- Last 10 transactions shown
- Direction indicators (↑ sent / ↓ received)
- Amount and status badge
- Timestamp for each transaction

**Flagged Activities Section**
- Transaction ID and Amount
- Fraud Score and Reason (AI explanation)
- Approve Button (complete transaction)
- Cancel Button (reject transaction)

**Credit Score Section**
- Current credit score display
- Credit rating badge
- AI-generated improvement tips

**Investment Portfolio Chart**
- Doughnut chart showing allocation
- Categories: Tech Stocks, Bonds, Crypto, Real Estate, Cash
- Interactive hover tooltips

**Balance Forecast Chart**
- Line chart with historical + projected data
- 14-day historical data with variance
- Linear regression projection for 14 days
- Interactive tooltips showing ₹ values

---

### 🎓 **Educational Features**

#### Fraud Simulations
Users can test fraud detection by simulating real attack vectors:

**Simulation Types:**
1. **Email Phishing**: Input suspicious email content
2. **SMS Smishing**: Test text message scams
3. **Phone Scams**: Analyze suspicious caller patterns

**Live Chat Log Feature:**
- Simulated conversation between victim and attacker
- Shows how social engineering unfolds
- Real-time message timestamps
- Educational breakdowns of tactics

---

### 🧠 **AI Financial Advisor Chatbot**

#### Overview
Interactive chatbot powered by Gemini AI that provides:
- Budget advice
- Investment guidance
- Credit score tips
- Savings strategies
- Debt management plans

#### Features

**Voice Input/Output**
- 🎤 Click microphone → speak question
- 🔊 Click "Listen" on any response → hear it read aloud
- Web Speech API integration

**Chat Interface**
- Message history maintained during session
- Conversation context preserved (last 10 messages)
- Typing indicator while AI responds
- Timestamps on each message
- User vs Bot visual distinction

**YouTube Recommendations**
- Relevant financial education videos shown with responses
- Video thumbnails with title and description
- Direct YouTube link with "Watch" button

**Markdown-Safe Output**
- Renders bold text: `**text**` → `<strong>text</strong>`
- Renders italic text: `*text*` → `<em>text</em>`
- Renders bullet lists: `- item` → `<ul><li>item</li></ul>`
- Escapes HTML to prevent injection attacks

---

### 📚 **Documentation Pages**

#### 1. API Documentation (`/api-docs`)
- Authentication methods
- Fraud Check Endpoint
- Rate Limiting (100 requests/hour)
- Error Codes (401, 403, 429, 500)
- Code Examples (cURL, Python, JavaScript)

#### 2. User Guide (`/user-guide`)
- Getting Started
- Setting up 2FA
- Sending Your First Transaction
- Understanding Fraud Scores
- Best Practices

#### 3. FAQ Page (`/faq`)
Getting Started | Account & Security | Transactions | Fraud Detection | Pricing & Plans | Support

**Pricing Tiers:**
| Tier | Monthly | Requests/Day | Users | Features |
|------|---------|-------------|-------|----------|
| **Free** | ₹0 | 100 | 1 | Basic detection, email support |
| **Starter** | ₹399 | 5,000 | 5 | Advanced detection, API, 24h support |
| **Pro** | ₹1,999 | 50,000 | 25 | AI models, webhooks, 4h support |
| **Enterprise** | ₹4,999 | Unlimited | ∞ | Custom AI, 24/7 support, 99.9% SLA |

#### 4. Contact Form (`/contact`)
- Name, Email, Subject, Message fields
- Support request tracking
- Email notification to support team

---

## 🛠️ Technology Stack

| Component | Technology |
|-----------|-----------|
| **Backend** | Flask 2.3.x |
| **Database** | SQLite 3.x |
| **ORM** | SQLAlchemy 2.0.x |
| **Frontend** | Bootstrap 5.3.x |
| **Charts** | Chart.js 4.4.x |
| **AI API** | Google Gemini 2.0 Flash |
| **Authentication** | Flask-Login 0.6.x |
| **2FA** | PyOTP 2.9.x |
| **Password Hashing** | Werkzeug 2.3.x |
| **Forms** | WTForms 3.x |
| **QR Codes** | qrcode 7.4.x |

---

## 🚀 Installation

### Prerequisites
- ✅ Python 3.8 or higher
- ✅ Git (for cloning repository)
- ✅ Google Gemini API key ([Get free key](https://makersuite.google.com/app/apikey))
- ✅ (Optional) Google Authenticator app for 2FA testing

### Step-by-Step Setup (Windows PowerShell)

#### 1. Clone Repository
```powershell
git clone https://github.com/YOUR_USERNAME/fraudguard.git
cd fraudguard
```

#### 2. Create Virtual Environment
```powershell
python -m venv .venv
```

#### 3. Activate Virtual Environment
```powershell
.\.venv\Scripts\Activate.ps1
```

If you get execution policy error:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
.\.venv\Scripts\Activate.ps1
```

#### 4. Upgrade pip
```powershell
python -m pip install --upgrade pip
```

#### 5. Install Dependencies
```powershell
pip install -r requirements.txt
```

#### 6. Set Gemini API Key

**Method A: Environment Variable (Recommended)**
```powershell
$env:GEMINI_API_KEY="your-api-key-here"
```

**Method B: Edit config.py**
```python
GEMINI_API_KEY = "your-api-key-here"
```

#### 7. Run Application
```powershell
python app.py
```

#### 8. Access Application
Open browser and navigate to:
```
http://127.0.0.1:5000
```

---

## ⚙️ Configuration

### config.py Reference

```python
class Config:
    SECRET_KEY                      # Flask session secret
    SQLALCHEMY_DATABASE_URI         # SQLite path
    GEMINI_API_KEY                  # Google Gemini API key
    YOUTUBE_API_KEY                 # YouTube Data API key (optional)
    INITIAL_BALANCE                 # Starting balance (default: ₹10,000)
    LARGE_TRANSACTION_THRESHOLD     # Fraud check trigger (default: 0.3 = 30%)
```

### Environment Variables
```powershell
$env:GEMINI_API_KEY = "your-key"
$env:YOUTUBE_API_KEY = "your-key"
$env:SECRET_KEY = "your-secret"
$env:DATABASE_URL = "sqlite:///custom_path/app.db"
```

---

## 📁 Project Structure

```
fraudguard/
├── app.py                          # Main Flask application (23 routes)
├── config.py                       # Configuration settings
├── models.py                       # Database models
├── forms.py                        # WTForms definitions
├── fraud_service.py                # Gemini AI integration
├── requirements.txt                # Python dependencies
├── README.md                       # This file
│
├── templates/                      # Jinja2 HTML templates (13 files)
│   ├── base.html                  # Layout with navbar/footer
│   ├── index.html                 # Homepage
│   ├── register.html              # Registration form
│   ├── login.html                 # Login with 2FA support
│   ├── setup_2fa.html             # 2FA setup with QR code
│   ├── new_dashboard.html         # Main user dashboard
│   ├── financial_advisor.html     # AI chatbot interface
│   ├── api_docs.html              # API documentation
│   ├── user_guide.html            # Integration guide
│   ├── faq.html                   # FAQ with pricing
│   ├── simulations.html           # Fraud simulation tool
│   └── contact.html               # Contact form
│
├── static/                         # Static assets
│   ├── styles.css                 # Custom CSS (1600+ lines)
│   └── app.js                     # Frontend JavaScript (400+ lines)
│
├── instance/                       # Instance folder (auto-created)
│   └── app.db                     # SQLite database
│
└── .venv/                         # Virtual environment (auto-created)
```

---

## 🗄️ Database Models

### User Model
```python
Fields: id, username, email, password_hash, totp_secret, two_fa_enabled
        balance, face_id_enabled, created_at, last_login

Methods: set_password(), check_password(), generate_totp_secret()
         get_totp_uri(), verify_totp()
```

### Transaction Model
```python
Fields: id, sender_id, receiver_id, amount, status
        fraud_score, fraud_reason, requires_review
        face_verified, created_at, completed_at, description

Statuses: pending, completed, flagged, cancelled
```

### FraudPattern Model
```python
Fields: id, pattern_type, pattern, description
        severity, source, created_at, updated_at
```

### SimulationLog Model
```python
Fields: id, user_id, simulation_type, input_data
        conversation (JSON), fraud_detected, fraud_score
        fraud_details, created_at
```

### APIToken Model
```python
Fields: id, user_id, token, name, created_at, last_used
```

### ContactMessage Model
```python
Fields: id, name, email, subject, message, created_at, resolved
```

---

## 🔌 API Endpoints

### Authentication Routes
- `POST /register` - Register new account
- `POST /login` - Login with optional 2FA
- `GET /logout` - Logout current user

### Account Management
- `GET/POST /setup-2fa` - Setup or verify 2FA

### Transaction Routes
- `GET /dashboard` - View user dashboard
- `POST /send-money` - Send money to another user
- `POST /transaction/<id>/approve` - Approve flagged transaction
- `POST /transaction/<id>/cancel` - Cancel flagged transaction

### Feature Routes
- `POST /api/chat` - Chat with AI financial advisor
- `GET/POST /run-simulation` - Run fraud detection simulation
- `GET /api-docs` - View API documentation
- `GET /user-guide` - View integration guide
- `GET /faq` - View FAQ with pricing
- `POST /contact` - Submit support request

---

## 👤 User Features

### Account Features
- ✅ Create account with username/email/password
- ✅ Secure login with 2FA option
- ✅ View and manage profile
- ✅ Download transaction history
- ✅ Enable face verification

### Transaction Features
- ✅ Send money to other users
- ✅ Receive payments from others
- ✅ View transaction history
- ✅ Review flagged transactions
- ✅ Approve/cancel suspicious transactions
- ✅ Add notes to transactions

### Dashboard Features
- ✅ Real-time balance display
- ✅ Transaction summary
- ✅ Flagged activities review
- ✅ Financial insights (AI-generated)
- ✅ Credit score with tips
- ✅ Investment portfolio chart
- ✅ Balance forecast chart

### Financial Advisor Features
- ✅ Chat with AI about finances
- ✅ Get personalized advice
- ✅ Voice input and output
- ✅ YouTube recommendations
- ✅ View conversation history

### Educational Features
- ✅ Run fraud simulations
- ✅ Analyze phishing emails
- ✅ Test smishing detection
- ✅ See real fraud patterns
- ✅ Learn from chat logs

---

## 👨‍💻 Developer Guide

### Adding New Features

#### 1. Add Database Model
```python
class MyModel(db.Model):
    __tablename__ = 'my_table'
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100))
    created_at = db.Column(db.DateTime, default=datetime.utcnow)
```

#### 2. Create Flask Route
```python
@app.route("/my-feature", methods=["GET", "POST"])
@login_required
def my_feature():
    if request.method == "POST":
        data = request.get_json()
        return jsonify({"success": True})
    return render_template("my_feature.html")
```

#### 3. Create HTML Template
```html
{% extends 'base.html' %}
{% block content %}
<div class="container">
    <h1>My Feature</h1>
    <!-- Your HTML here -->
</div>
{% endblock %}
```

#### 4. Add Styling
```css
.my-feature {
    /* Your CSS */
}
```

### Extending Fraud Detection
```python
def analyze_new_data_type(self, content):
    """New fraud analysis method"""
    prompt = f"Analyze this content for fraud..."
    try:
        response = self.model.generate_content(prompt)
        return self._parse_gemini_response(response.text)
    except Exception as e:
        print(f"Gemini error: {e}")
        traceback.print_exc()
        return self._fallback_analysis(content, 'new_type')
```

### Customizing UI Theme
Edit CSS variables in `static/styles.css`:
```css
:root {
    --primary: #667eea;           /* Main brand color */
    --primary-hover: #5568d3;     /* Hover state */
    --bg-primary: #ffffff;        /* Main background */
    --bg-secondary: #f7fafc;      /* Secondary background */
    --text-primary: #1a202c;      /* Primary text */
}
```

---

## 🐛 Troubleshooting

### "Gemini API key not found"
```
1. Get API key from: https://makersuite.google.com/app/apikey
2. Set environment variable: $env:GEMINI_API_KEY="your-key"
3. Or update config.py: GEMINI_API_KEY = "your-key"
4. Restart the application
```

### "404 models/gemini-1.5-flash is not found"
```
The code auto-falls back through:
├─ gemini-2.0-flash-exp (preferred)
├─ models/gemini-1.5-flash (fallback)
└─ models/gemini-1.5-pro (final fallback)

Check console output to see which model initialized successfully.
```

### "Webcam permission denied"
```
1. Check browser permissions for camera
2. Use HTTPS in production (required)
3. Test fallback mode works (auto-verify)
4. Run simulations instead
```

### "Database locked" or SQLite errors
```
1. Close all other connections to app.db
2. Delete instance/app.db
3. Restart application (recreates DB)
4. Or: $env:DATABASE_URL="sqlite:///./my_db.db"
```

### "2FA not working"
```
1. Check system time (TOTP is time-based)
2. Verify code within 30-second window
3. Test with code from authenticator app
4. Check totp_secret is saved in database
```

### "Balance not updating after transaction"
```
1. Check database connection
2. Verify recipient user exists
3. Check sufficient balance available
4. Review app.py send_money route logic
5. Check fraud_service for errors
```

### "Charts not displaying"
```
1. Check Chart.js is loaded (network tab)
2. Verify canvas elements exist in HTML
3. Check browser console for JavaScript errors
4. Ensure data is available from Flask
5. Try browser refresh (clear cache)
```

---

## 🤝 Contributing

We welcome contributions! Here's how to help:

### Bug Reports
```
Title: Clear description of bug
Description:
├─ Steps to reproduce
├─ Expected behavior
├─ Actual behavior
└─ Screenshots/error logs
```

### Feature Requests
```
Title: Feature name
Description:
├─ Why it's needed
├─ How it should work
├─ Suggested implementation
└─ Related issues
```

### Code Contributions
```
1. Fork repository
2. Create feature branch: git checkout -b feature/my-feature
3. Make changes with clear commit messages
4. Test thoroughly
5. Submit pull request with description
```

### Style Guide
**Python:** Follow PEP 8, use type hints, add docstrings
**JavaScript:** Use const/let, add comments, test in multiple browsers
**CSS:** Use CSS variables, mobile-first approach, test responsiveness

---

## 📄 License

This project is licensed under the MIT License - see LICENSE file for details.

---

## 📞 Support

**Need help?**
- 📧 Email: support@fraudguard.com
- 💬 Use contact form: /contact
- 📖 Check FAQ: /faq
- 📚 Read docs: /user-guide

---

## 🙏 Acknowledgments

- Google Gemini AI for fraud detection
- Bootstrap for responsive UI
- Chart.js for beautiful visualizations
- Flask community for excellent documentation
- Open source community for libraries and tools

---

## 📊 Statistics

```
Total Lines of Code:     ~3,500+
Templates:               13
Routes:                  23
Database Models:         6
API Endpoints:           15+
JavaScript Functions:    40+
CSS Classes:             200+
Documentation Pages:     5
```

---

**Happy Fraud Prevention! 🛡️**

*Last Updated: November 2, 2025*
*Version: 1.0.0*
