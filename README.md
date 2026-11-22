<div align="center">

# 📚 StudySync Tasks

**A cloud-based, real-time task manager built for student project teams.**

Create courses, invite teammates, assign tasks, and watch progress update live — no refresh needed.

![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)
![Firestore](https://img.shields.io/badge/Cloud_Firestore-FF6F00?style=for-the-badge&logo=firebase&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)

</div>

---

## 📌 Table of Contents
- [About](#-about)
- [Features](#-features)
- [Screenshots](#-screenshots)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [How It Works](#-how-it-works)
- [Getting Started](#-getting-started)
- [Security](#-security)
- [Limitations & Future Work](#-limitations--future-work)
- [Team](#-team)

---

## 💡 About

Most to-do apps are built for individuals. Student group projects need something different: one shared place where everyone can see **who is doing what, and by when**.

**StudySync Tasks** is a single-page web app where students group their work by course, invite classmates by email, and manage tasks together. Every change is synced instantly to all members through Cloud Firestore real-time listeners.

> Developed as the course project for **CS355 – Cloud Computing**, Imam Mohammad Ibn Saud Islamic University (Fall 2025).

---

## ✨ Features

| | Feature | Description |
|---|---|---|
| 🔐 | **Secure Authentication** | Sign up / log in with email & password, with mandatory email verification |
| 📘 | **Course Management** | Create courses and invite members by email |
| ✅ | **Task Management (CRUD)** | Create, edit, delete and assign tasks |
| 🎯 | **Priority & Due Dates** | Set priority (Low / Medium / High), status and deadline per task |
| 🔎 | **Filter & Sort** | Filter by status; sort by due date or creation date |
| ⚡ | **Real-Time Sync** | Changes appear instantly for every team member |

---

## 🖼 Screenshots

| Dashboard | Add New Task |
|---|---|
| ![Dashboard](Screenshot%202026-11-22%20194548.png) | ![Add task](Screenshot%202026-11-22%20194615.png) |

| Sort Tasks | Filter Tasks |
|---|---|
| ![Sort](Screenshot%202026-11-22%20194659.png) | ![Filter](Screenshot%202026-11-22%20194726.png) |

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React (Hooks), React Router DOM |
| Authentication | Firebase Authentication (Email/Password + email verification) |
| Database & Sync | Cloud Firestore (NoSQL, real-time listeners) |
| Hosting | Firebase Hosting |
| Tooling | Node.js, npm, Firebase CLI |

---

## 🏗 Architecture

```
┌──────────────────────┐        ┌───────────────────────────┐
│   React SPA (Client) │◀──────▶│  Firebase Authentication  │
│  - Auth pages        │        └───────────────────────────┘
│  - Dashboard         │        ┌───────────────────────────┐
│  - Course / Tasks    │◀──────▶│  Cloud Firestore          │
└──────────┬───────────┘ live   │  courses / tasks          │
           │          listeners └───────────────────────────┘
           ▼
┌──────────────────────┐
│   Firebase Hosting   │
└──────────────────────┘
```

---

## 🔄 How It Works

1. **Sign up** → a verification email is sent → the user verifies the account.
2. **Log in** → land on the dashboard showing all courses the user belongs to.
3. **Create a course** → add a name, description and members' emails.
4. **Add tasks** → title, description, assignee, priority, status and due date.
5. **Organize** → mark tasks complete/incomplete, filter and sort.
6. **Collaborate** → every update is pushed live to all members.

---

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ and npm
- A Firebase project with **Authentication**, **Firestore** and **Hosting** enabled

### 1. Clone & install
```bash
git clone https://github.com/NAZ1z/StudySync-Tasks-.git
cd StudySync-Tasks-
npm install
```

### 2. Configure Firebase
Create a `.env` file in the project root:
```env
REACT_APP_FIREBASE_API_KEY=your_api_key
REACT_APP_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
REACT_APP_FIREBASE_PROJECT_ID=your_project_id
REACT_APP_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
REACT_APP_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
REACT_APP_FIREBASE_APP_ID=your_app_id
```

In the Firebase Console:
- **Authentication → Sign-in method:** enable *Email/Password*
- **Firestore:** create a database and apply the security rules shown below

### 3. Run locally
```bash
npm start
```
Open http://localhost:3000

### 4. Deploy (optional)
```bash
npm run build
npm install -g firebase-tools
firebase login
firebase init hosting
firebase deploy --only hosting
```

---

## 🔒 Security

Firestore access is restricted to authenticated users:

```js
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

> 🔧 Planned improvement: scope rules so users can only access courses they are members of.

---

## 🧭 Limitations & Future Work

- [ ] Per-course access rules in Firestore
- [ ] In-app notifications for new assignments and approaching deadlines
- [ ] Task comments and file attachments
- [ ] Mobile-optimized layout

---

## 👩‍💻 Team

| Name | GitHub |
|---|---|
| Nazek Alzaid | [@NAZ1z](https://github.com/NAZ1z) |
| Nawt Alotaibi | — |
| Shahad Alrashidi | — |
| Raghad Bin Thwaini | — |

**Supervised by:** Dr. Jaben Sultana — CS355 Cloud Computing

---

<div align="center">
⭐ If you find this project useful, consider giving it a star!
</div>
