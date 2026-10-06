# 🏙️ CityCare – Smart Civic Issue Management Platform

CityCare is a **MERN-stack based civic issue reporting and management platform** that connects citizens with municipal administrators and field officers.

The platform enables citizens to report civic issues such as **road damage, garbage accumulation, streetlight failures, drainage problems, water supply issues, and other public-service complaints**. Administrators can verify, assign, monitor, and resolve complaints through a structured and transparent workflow.

---

## 📌 About the Project

In many cities, citizens face difficulties while reporting civic problems and tracking their resolution. At the same time, municipal authorities need an organized system to manage complaints, assign responsible officers, monitor deadlines, and evaluate department performance.

**CityCare** provides a centralized platform for managing the complete lifecycle of a civic complaint.

The system supports:

* Citizen complaint reporting
* Complaint verification
* Department and officer assignment
* Real-time status tracking
* SLA/deadline monitoring
* Complaint escalation
* Evidence-based resolution
* Citizen feedback and ratings
* Administrative analytics
* Location-based complaint visualization
* Role-based access control

The goal is to make civic issue management **transparent, accountable, and easier to monitor**.

---

## ✨ Key Features

### 👤 Citizen Module

* User registration and login
* Secure JWT-based authentication
* Report civic issues
* Upload complaint images
* Select complaint category and department
* Add issue description
* Provide issue location
* Track complaint status
* View complaint history
* Communicate with assigned officers
* Reopen unresolved/recurring complaints
* Withdraw complaints before verification
* Submit feedback and ratings

---

### 🏢 City Administrator Module

* Admin dashboard
* View and filter city-wide complaints
* Verify or reject complaints
* Assign complaints to field officers
* Reassign officers when required
* Change complaint priority/category
* Monitor SLA deadlines
* Handle escalated complaints
* Review resolution evidence
* Request rework from field officers
* Monitor department performance
* View complaint statistics
* Monitor complaints on a city map
* View system audit logs

---

### 👷 Field Officer Module

* Officer dashboard
* View assigned complaints
* Accept assigned tasks
* Update complaint progress
* Add work/resolution details
* Upload resolution evidence
* Mark complaints for verification
* Respond to citizen queries
* Track pending and completed assignments

---

### 🔐 Authentication & Authorization

CityCare uses **role-based access control (RBAC)** to provide different permissions to different users.

```text
Citizen
   ↓
Report & Track Issues

Field Officer
   ↓
Manage Assigned Issues

City Admin
   ↓
Verify, Assign & Monitor Issues

System Admin
   ↓
Manage Platform & Cities
```

Authentication is implemented using:

* JWT
* bcrypt/bcryptjs
* Protected routes
* Role-based authorization

---

# 🔄 Issue Workflow

## Primary Lifecycle

```text
Pending
   ↓
Verified
   ↓
Assigned
   ↓
In Progress
   ↓
Pending Verification
   ↓
Resolved
   ↓
Closed
```

## Exception States

```text
Pending
 ├── Rejected
 ├── Withdrawn
 └── Verified
       ↓
    Assigned
       ↓
    In Progress
       ↓
    Rework Required
       ↓
    Resolved
       ↓
    Reopened
       ↓
    In Progress
```

### Status Description

| Status               | Description                                  |
| -------------------- | -------------------------------------------- |
| Pending              | Complaint submitted by citizen               |
| Verified             | Complaint verified by administrator          |
| Rejected             | Invalid or insufficient complaint            |
| Assigned             | Complaint assigned to an officer             |
| In Progress          | Officer is working on the issue              |
| Pending Verification | Resolution submitted for verification        |
| Rework Required      | Additional work/evidence required            |
| Resolved             | Issue has been resolved                      |
| Closed               | Complaint successfully completed             |
| Reopened             | Citizen reports that the issue still exists  |
| Escalated            | Complaint requires higher-level intervention |
| Withdrawn            | Complaint withdrawn by citizen               |

---

# ⚙️ Core Algorithms

CityCare includes several rule-based algorithms to improve complaint management.

### 1. Duplicate Complaint Detection

The system can identify potentially duplicate complaints using factors such as:

* Complaint category
* Description similarity
* Geographical proximity
* Recent submission time

This helps reduce repeated complaints for the same civic issue.

---

### 2. Geographical Distance Calculation

The **Haversine Formula** can be used to calculate the distance between two geographical coordinates.

This can help in:

* Finding nearby complaints
* Assigning nearby officers
* Displaying complaints on maps

---

### 3. Officer Assignment

Complaints can be assigned based on:

```text
Department
     +
Complaint Category
     +
Officer Availability
     +
Location / Distance
     ↓
Suitable Field Officer
```

---

### 4. SLA & Escalation

Every complaint can have a defined resolution deadline.

```text
Complaint Created
       ↓
SLA Timer Starts
       ↓
Officer Assigned
       ↓
Issue In Progress
       ↓
Deadline Approaching
       ↓
Escalation
```

If an issue crosses its defined SLA deadline, it can automatically be marked for escalation.

---

### 5. Officer Performance Analysis

Performance can be calculated using metrics such as:

* Assigned complaints
* Resolved complaints
* Average resolution time
* SLA compliance
* Rework requests
* Citizen ratings

---

### 6. Citizen Rate Limiting

Rate limiting can be implemented to prevent excessive complaint submissions and reduce system abuse.

---

# 🛠️ Tech Stack

## Frontend

* React.js
* React Router
* JavaScript
* HTML5
* CSS3
* Tailwind CSS
* Axios
* Recharts

## Backend

* Node.js
* Express.js
* REST APIs
* JWT Authentication
* bcrypt/bcryptjs

## Database

* MongoDB
* Mongoose

## Maps & Location

* Leaflet
* OpenStreetMap

## File Storage

* Cloudinary *(optional)*

## Real-Time Communication

* Socket.IO *(optional)*

## Development Tools

* Git
* GitHub
* VS Code
* Postman
* npm

---

# 🏗️ Project Architecture

```text
CityCare/
│
├── client/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── layouts/
│   │   ├── hooks/
│   │   ├── services/
│   │   ├── context/
│   │   ├── utils/
│   │   └── App.jsx
│   │
│   └── package.json
│
├── server/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── services/
│   ├── utils/
│   ├── config/
│   ├── uploads/
│   └── server.js
│
├── .gitignore
├── README.md
└── package.json
```

---

# 🗄️ Database Design

The application can use the following MongoDB collections:

```text
users
complaints
departments
categories
assignments
comments
notifications
feedback
auditLogs
slaRules
cities
```

### Main Relationships

```text
User
 ├── Complaints
 ├── Comments
 ├── Feedback
 └── Notifications

Complaint
 ├── Category
 ├── Department
 ├── Assigned Officer
 ├── Comments
 ├── Evidence
 ├── Feedback
 └── Audit Logs
```

---

# 🚀 Getting Started

## Prerequisites

Make sure the following are installed:

* Node.js
* npm
* Git
* MongoDB / MongoDB Atlas
* Code editor such as VS Code

Optional services:

* Cloudinary
* Socket.IO
* Leaflet/OpenStreetMap

---

## 📥 Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

```bash
cd CityCare
```

---

## 📦 Install Dependencies

### Install Backend Dependencies

```bash
cd server
npm install
```

### Install Frontend Dependencies

```bash
cd ../client
npm install
```

---

# 🔑 Environment Variables

Create a `.env` file inside the `server` directory.

```env
PORT=5000

MONGO_URI=your_mongodb_connection_string

JWT_SECRET=your_jwt_secret

CLIENT_URL=http://localhost:5173

# Optional
CLOUDINARY_CLOUD_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
```

> **Important:** Never commit `.env` files or secret credentials to GitHub.

---

# ▶️ Running the Application

Start the backend:

```bash
cd server
npm run dev
```

Start the frontend in another terminal:

```bash
cd client
npm run dev
```

The application will normally be available at:

```text
http://localhost:5173
```

The backend API will normally run at:

```text
http://localhost:5000
```

---

# 🔌 REST API Structure

Example API structure:

```text
/api/auth
/api/users
/api/complaints
/api/departments
/api/categories
/api/officers
/api/assignments
/api/comments
/api/feedback
/api/notifications
/api/analytics
```

### Example Complaint APIs

```text
POST   /api/complaints
GET    /api/complaints
GET    /api/complaints/:id
PUT    /api/complaints/:id
DELETE /api/complaints/:id
PATCH  /api/complaints/:id/status
PATCH  /api/complaints/:id/assign
POST   /api/complaints/:id/comments
POST   /api/complaints/:id/feedback
```

---

# 📊 Admin Dashboard

The administrative dashboard can provide:

* Total complaints
* Pending complaints
* Verified complaints
* In-progress complaints
* Resolved complaints
* Escalated complaints
* SLA compliance
* Department-wise statistics
* Officer performance
* Complaint category distribution
* Monthly complaint trends
* Location-based complaint visualization

Example:

```text
Total Complaints       : 1,250
Pending                : 180
In Progress            : 320
Resolved               : 690
Escalated              : 60
Average Resolution     : 3.2 Days
SLA Compliance         : 87%
```

---

# 🔒 Security

CityCare follows standard web application security practices:

* JWT-based authentication
* Password hashing using bcrypt
* Role-based authorization
* Protected API routes
* Input validation
* Environment variables for secrets
* Rate limiting
* Secure error handling
* Audit logging

---

# 🌐 Deployment

The application can be deployed using services such as:

### Frontend

* Vercel
* Netlify

### Backend

* Render
* Railway
* AWS

### Database

* MongoDB Atlas

Before deployment, configure the required environment variables and update the frontend/backend API URLs.

---

# 🔮 Future Enhancements

Possible future improvements include:

* Mobile application
* Push notifications
* Advanced GIS-based analytics
* Ward-level dashboards
* Public complaint heatmaps
* QR-based complaint tracking
* Multilingual interface
* Digital certificates for civic contributors
* Advanced notification system
* Government department integrations

---

# 🎯 Project Objectives

The major objectives of CityCare are:

1. Digitize civic issue reporting.
2. Improve communication between citizens and authorities.
3. Provide transparent complaint tracking.
4. Reduce duplicate and invalid complaints.
5. Improve officer accountability.
6. Monitor SLA deadlines.
7. Provide useful administrative analytics.
8. Improve the overall civic issue resolution process.

---

# 👨‍💻 Project Typ
