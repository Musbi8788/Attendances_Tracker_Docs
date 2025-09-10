# Internal Documentation – MyFarm Attendance Tracker

## Project Name:
**MyFarm Attendance Tracker**

## Developed by:
**Musbi Jawo**  
August 2025  
Internal Project for MyFarm

---

## Overview
The **MyFarm Attendance Tracker** is a digital system built to simplify and secure attendance tracking for **MyFarm’s interns, students, and staff**. It replaces manual methods and prevents cheating by requiring a **webcam snapshot** with every sign-in/out.

---

## Objective
- Prevent impersonation during attendance
- Improve accountability and data tracking
- Allow real-time access to attendance records by both users and admins

---

## Access Roles

### General Users (Staff, Interns, Students)
- Register and log in with username + password
- Sign in/out with **webcam snapshot**
- View personal attendance records
- View personal history records


### Admins
- Separate admin interface
- View all attendance logs with filters
- Reset user passwords
- Export full attendance logs
- Export all data as CSV
- Future features: add users manually, receive notifications

---

## Technologies Used

| Layer        | Tool                                |
|--------------|-------------------------------------|
| Backend      | Flask (Python)                      |
| Frontend     | HTML, CSS, Bootstrap JavaScript     |
| Camera       | Browser (WebcamJS)                  |
| Database     | SQLite                              |
| Storage      | Local server (images)               |
| Deployment   | Render                              |
| Compatibility| Works on all browsers               |

---

## Mobile Friendly
Yes – fully responsive and usable across mobile phones and tablets.

---

## System Workflow

1. **User Registration**
   - Users self-register with name + email + phone + ID + password
   - Admin resets passwords if needed

2. **Sign In / Out**
   - User logs in
   - Clicks **Sign In** or **Sign Out**
   - Webcam activates and captures image
   - Timestamp and image are stored in the database

3. **Admin Interface**
   - Admin logs in via separate admin route
   - Admin can view all records, filter, reset passwords, export data

---

## Installation (Development Setup)

```bash
git clone [PRIVATE_REPO_URL]
cd attendance-tracker
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
python main.py
```

---

## Deployment Details

- Live Link: [https://attendace-tracker-v0-1.onrender.com/](https://attendace-tracker-v0-1.onrender.com/)
- Host: Render.com
- Python version: 3.10+
- Start command (on Render):  
  ```bash
  gunicorn main:app
  ```

---

## File Structure (Important Files)

```
/static/         → CSS, JS, camera script
/templates/      → HTML pages
/uploads/        → Saved webcam images (per user)
main.py           → Main Flask logic
auth.py          → Registration/login/reset logic
admin.py         → Admin routes & views
models.py        → SQLite database models
utils.py         → Time/image handling
requirements.txt → Project dependencies
```

---

## Data Export
- Users and Admins can export attendance logs as `.csv` files

---

## Security & Privacy
- Users must grant camera access to use the app
- All image and attendance data is private and stored locally
- Only admins can access global logs and reset passwords

---

## Planned Features

| Feature | Description |
|--------|-------------|
| ✅ Password reset by users | Let users reset forgotten passwords securely |
| ✅ Admin user creation | Allow admin to manually create user accounts |
| 🔔 Missed sign-out alerts | Notify users/admins when a user forgets to sign out after work hours |
| 🤖 Assistant bot | Guide users with chatbot or FAQ popup |
| ☁️ Cloud image storage | Move snapshots to cloud (e.g., Cloudinary) for scalability |
| 📱 Progressive Web App (PWA) | Make it installable like a native mobile app |

---

## Audience & Usage
This system is actively used by:
- **MyFarm CEO**
- **Staff**
- **Interns**
- **Students**

All users are expected to sign in/out daily through the system.

---

## Notes for CEO & Team
- The system is live and stable
- All sign-ins are verified with images
- Logs can be exported or viewed by date, user, or role
- Backups of the SQLite database and image folder should be done weekly
