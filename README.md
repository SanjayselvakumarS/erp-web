# College ERP System - Complete Setup Guide

## 🎯 Overview

The College ERP system now has a **Django REST API backend** with a **modern web frontend**. The system uses JWT authentication and provides role-based dashboards for Students, Teachers, and Admins...

## 📁 Project Structure

```
ERP APP/
├── backend/                  # Django REST API
│   ├── manage.py
│   ├── requirements.txt
│   ├── setup.bat            # Windows setup script
│   ├── setup.sh             # Linux/Mac setup script
│   ├── college_erp/         # Django project
│   └── api/                 # Django app
└── web/                     # Frontend
    ├── index.html           # Login page
    ├── css/                 # Styles
    ├── js/
    │   ├── api-client.js    # API client with JWT
    │   ├── auth.js          # Authentication
    │   └── utils.js         # Utilities
    ├── student/             # Student dashboard
    ├── teacher/             # Teacher dashboard
    └── admin/               # Admin dashboard
```

## 🚀 Quick Start

### Step 1: Setup Django Backend

**Windows:**
```bash
cd "d:\PROJECTS\flutter app\ERP APP\backend"
setup.bat
```

**Linux/Mac:**
```bash
cd "d:/PROJECTS/flutter app/ERP APP/backend"
chmod +x setup.sh
./setup.sh
```

**Manual Setup:**
```bash
cd backend
python -m venv venv
venv\Scripts\activate          # Windows
# source venv/bin/activate     # Linux/Mac
pip install -r requirements.txt
python manage.py makemigrations
python manage.py migrate
python manage.py seed_data
python manage.py runserver
```

The API will run on: `http://localhost:8000/api/`

### Step 2: Open Frontend

**Option 1: Using Live Server (Recommended)**
1. Install "Live Server" extension in VS Code
2. Right-click on `web/index.html`
3. Select "Open with Live Server"

**Option 2: Using Python HTTP Server**
```bash
cd web
python -m http.server 8080
```
Then open: `http://localhost:8080/index.html`

**Option 3: Direct File Access**
Open `d:\PROJECTS\flutter app\ERP APP\web\index.html` in your browser

> **Note:** For API calls to work, the Django backend must be running!

## 🔐 Demo Credentials

| Role | Email | Password |
|------|-------|----------|
| **Student** | student@college.edu | student123 |
| **Teacher** | teacher@college.edu | teacher123 |
| **Admin** | admin@college.edu | admin123 |

## ✨ Features

### Student Dashboard
- ✅ View overall and subject-wise attendance
- ✅ Check marks and grades
- ✅ Pay college fees online
- ✅ Download payment receipts
- ✅ View announcements

### Teacher Dashboard
- ✅ Mark student attendance
- ✅ Enter and update marks
- ✅ View assigned classes
- ✅ Post announcements
- ✅ Manage class rosters

### Admin Dashboard
- ✅ Manage students and teachers
- ✅ Create and manage subjects
- ✅ Configure fee structures
- ✅ Track payment collections
- ✅ Generate attendance and fee reports
- ✅ Export reports to CSV

## 🔧 Technical Stack

### Backend
- **Framework:** Django 5.0.1
- **API:** Django REST Framework 3.14.0
- **Authentication:** JWT (djangorestframework-simplejwt)
- **Database:** SQLite (development) / PostgreSQL (production)
- **CORS:** django-cors-headers

### Frontend
- **HTML5, CSS3, JavaScript** (Vanilla)
- **JWT Token Management**
- **Responsive Design**
- **Modern UI with Glassmorphism**

## 📡 API Endpoints

### Authentication
- `POST /api/auth/login/` - Login
- `POST /api/auth/logout/` - Logout
- `POST /api/auth/refresh/` - Refresh token
- `GET /api/auth/me/` - Current user

### Student
- `GET /api/student/dashboard/` - Overview stats
- `GET /api/student/attendance/` - Attendance
- `GET /api/student/marks/` - Marks
- `GET /api/student/fees/pending/` - Pending fees
- `POST /api/student/fees/pay/` - Pay fee

### Teacher
- `GET /api/teacher/dashboard/` - Overview stats
- `GET /api/teacher/subjects/` - Subjects
- `POST /api/teacher/attendance/mark/` - Mark attendance
- `POST /api/teacher/marks/` - Enter marks
- `POST /api/teacher/announcements/` - Create announcement

### Admin
- `GET /api/admin/dashboard/` - System stats
- `GET /api/admin/users/` - List users
- `POST /api/admin/users/` - Create user
- `DELETE /api/admin/users/` - Delete user
- `GET /api/admin/reports/attendance/` - Attendance report
- `GET /api/admin/reports/fees/` - Fee report

## 🔍 Troubleshooting

### CORS Errors
If you see CORS errors in the browser console:
1. Make sure Django backend is running
2. Check that `CORS_ALLOW_ALL_ORIGINS = True` in `backend/college_erp/settings.py`
3. Verify the API_BASE_URL in `web/js/api-client.js` is correct

### Login Issues
1. Ensure Django backend is running on `http://localhost:8000`
2. Check browser console for errors
3. Verify demo data was seeded: `python manage.py seed_data`

### Token Expired
- Access tokens expire after 1 hour
- The system automatically refreshes tokens
- If refresh fails, you'll be redirected to login

## 📊 Database Management

### View Data (Django Admin)
```bash
python manage.py createsuperuser
```
Then visit: `http://localhost:8000/admin/`

### Reset Database
```bash
python manage.py flush
python manage.py seed_data
```

### Backup Database
```bash
python manage.py dumpdata > backup.json
```

## 🚀 Production Deployment

### Backend
1. Set `DEBUG=False` in `.env`
2. Configure PostgreSQL database
3. Set proper `SECRET_KEY`
4. Configure allowed hosts
5. Use gunicorn/uwsgi
6. Set up nginx reverse proxy
7. Enable HTTPS

### Frontend
1. Build and minify assets
2. Deploy to static hosting (Netlify, Vercel, etc.)
3. Update API_BASE_URL to production API
4. Configure CORS on backend

## 📝 Development Notes

- **Frontend uses JWT tokens** stored in localStorage
- **Automatic token refresh** when access token expires
- **Role-based access control** on both frontend and backend
- **Demo data** includes 1 student, 1 teacher, 1 admin
- **All passwords** are stored in plain text for demo (hash in production!)

## 🤝 Support

For issues:
1. Check browser console for errors
2. Check Django server logs
3. Verify backend is running
4. Ensure demo data is seeded

## 📚 Documentation

- **Backend README:** `backend/README.md`
- **API Documentation:** Available at backend endpoints
- **Walkthrough:** See artifacts folder for detailed feature walkthrough

---

**Built with ❤️ for College ERP Management**
