# Flask Authentication Starter

A clean, secure Flask application with user authentication featuring:

## ✨ Features

- **Secure Authentication**: Registration and login with Werkzeug password hashing
- **Username Normalization**: Usernames are lowercase and case-insensitive
- **Strong Validation**: 
  - Username: 3-20 chars, alphanumeric + underscore only
  - Email: Valid email format required
  - Password: Minimum 8 characters
- **Responsive Design**: Bootstrap 5 navbar layout works on all devices
- **Flash Messages**: User-friendly feedback for all actions
- **Protected Routes**: Dashboard only accessible when logged in
- **Session Management**: Flask-Login handles user sessions securely

## 🚀 Quick Start (Windows PowerShell)

```powershell
# Create virtual environment
python -m venv .venv

# Activate virtual environment
.\.venv\Scripts\Activate.ps1

# Install dependencies
pip install -U pip
pip install -r requirements.txt

# Run the application
python app.py
```

Navigate to: **http://127.0.0.1:5000**

## 📁 Project Structure

```
├── app.py              # Main application (models, forms, routes)
├── requirements.txt    # Python dependencies
├── templates/          # HTML templates (Jinja2)
│   ├── base.html       # Base layout with navbar
│   ├── index.html      # Homepage
│   ├── login.html      # Login form
│   ├── register.html   # Registration form
│   └── dashboard.html  # Protected user dashboard
└── static/
    └── styles.css      # Custom CSS
```

## 🔒 Security Notes

- **SECRET_KEY**: Change `app.config['SECRET_KEY']` to a secure random value in production
- **Database**: Uses SQLite (`app.db`) for development. Switch to PostgreSQL/MySQL for production
- **HTTPS**: Always use HTTPS in production to protect credentials in transit
- **Password Hashing**: Werkzeug's `generate_password_hash()` uses secure defaults

## 📝 User Restrictions

- **Username**: 3-20 characters, letters/numbers/underscore only, automatically lowercased
- **Email**: Must be valid email format, unique
- **Password**: Minimum 8 characters (no maximum for security)
- All usernames and emails are case-insensitive for consistency

## 🎨 Responsive Layout

The Bootstrap 5 navbar automatically adapts:
- **Desktop**: Horizontal menu
- **Mobile**: Collapsible hamburger menu
- **Tablet**: Optimized for medium screens
