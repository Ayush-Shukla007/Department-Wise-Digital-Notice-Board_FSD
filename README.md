# 📌 Department-Wise Digital Notice Board (FSD) — ABESEC Ghaziabad

[![React](https://img.shields.io/badge/React-18-blue.svg?logo=react)](https://react.dev/)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow.svg?logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![Render](https://img.shields.io/badge/Deploy-Render%20Static%20Site-46E3B7?logo=render&logoColor=white)](https://department-wise-digital-notice-board-fsd.onrender.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A centralized, responsive, and interactive **Department-Wise Digital Notice Board** web application built for **ABESEC Ghaziabad**. It enables departments to publish, categorize, search, bookmark, and display institutional announcements, exam timetables, academic calendars, and placement updates in real time.

---

## 🌐 Live Deployment (Render)

- **Deployed Render URL:** [https://department-wise-digital-notice-board-fsd.onrender.com](https://department-wise-digital-notice-board-fsd.onrender.com)

---

## 🔐 User Login Credentials

All demo user roles below are pre-configured and ready to use on the portal:

| Role | Username (Email) | Password | Department |
| :--- | :--- | :--- | :--- |
| **Admin** | `admin@abesec.ac.in` | `Admin@123` | CSE |
| **Student** | `student@abesec.ac.in` | `Student@123` | CSE |
| **Student (Google SSO)** | `student@google.edu` | `password123` | Selected Dept |
| **Student (College Portal SSO)** | `student@portal.edu` | `password123` | Selected Dept |

### Credentials by Role

- **Admin Role**
  - **Admin Username:** `admin@abesec.ac.in`
  - **Admin Password:** `Admin@123`
- **Student Role**
  - **Student Username:** `student@abesec.ac.in`
  - **Student Password:** `Student@123`
- **Quick SSO Demo Accounts**
  - Click **Google SSO** (`student@google.edu` / `password123`) or **College Portal** (`student@portal.edu` / `password123`) on the login screen for one-click access.
  - New users can also register via the **Sign up** toggle on the login page.

---

## 📖 Table of Contents

- [Live Deployment (Render)](#-live-deployment-render)
- [User Login Credentials](#-user-login-credentials)
- [Overview](#-overview)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Deploying on Render](#-deploying-on-render)
- [Team & Institution](#-team--institution)
- [License](#-license)

---

## 🌟 Overview

The **Department-Wise Digital Notice Board** is a Full-Stack Development (FSD) project engineered for **ABESEC Ghaziabad** to modernize campus communication. In colleges and universities, physical notice boards are often cluttered, inefficient, and inaccessible remotely. This web platform provides a clean, role-aware, department-filtered digital hub where students and faculty can view verified institutional notices anytime, anywhere.

---

## 🚀 Key Features

- 🏢 **Department-Wise Segmentation**: Filter notices across **CSE**, **IT**, **ECE**, **ME**, **Training & Placement (T&P)**, and **Exam Cell (EXAM)**.
- 🔐 **Multi-Role Authentication**: Supports pre-seeded **Admin** and **Student** accounts, **Sign Up**, **Remember Me** session persistence, and one-click **SSO** demo login.
- 📊 **Interactive Dashboard & Portal**: Overview stats (total, unread, upcoming events, saved), pinned/important highlights, and real-time notification bell.
- 📅 **Exam Timetable & Academic Calendar**: Dedicated tabs for exam schedules and an interactive monthly academic calendar with event & deadline markers.
- 🔖 **Bookmarks, Read Status & Dark Mode**: Save notices, mark read/unread, compact view toggle, and light/dark theme persistence via `localStorage`.
- 🔍 **Instant Search & Filtering**: Filter by department, category, read status, tags, and sort order.
- 📱 **Responsive Design**: Works across desktops, tablets, and mobile screens.

---

## 🛠️ Tech Stack

- **React 18** (Standalone CDN setup with Babel JSX transpiler)
- **HTML5** & semantic markup
- **CSS3** (Custom properties, Flexbox, CSS Grid, light/dark themes)
- **JavaScript (ES6+)** with `localStorage` & `sessionStorage` state persistence

---

## 📂 Project Structure

```text
Department-Wise-Digital-Notice-Board_FSD/
├── .gitignore              # Files and directories ignored by Git
├── index.html              # Main frontend entry point, styles, and React components
├── render.yaml             # Render Static Site Blueprint configuration
└── README.md               # Project documentation, deployment URL, and login credentials
```

---

## ⚡ Getting Started

### Prerequisites

All you need is a modern web browser (Google Chrome, Microsoft Edge, Mozilla Firefox, or Brave).

### Running Locally

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Ayush-Shukla007/Department-Wise-Digital-Notice-Board_FSD.git
   cd Department-Wise-Digital-Notice-Board_FSD
   ```

2. **Open the project:**
   - Double-click `index.html` to open it directly in your browser, or
   - Serve locally with any static server (e.g., `npx serve .` or VS Code **Live Server**).

---

## ☁️ Deploying on Render

This repository includes a [`render.yaml`](render.yaml) Blueprint configured for Render Static Site hosting:

1. Log in to [Render](https://dashboard.render.com/) and click **New +** → **Static Site** (or **Blueprint**).
2. Connect the GitHub repository `Ayush-Shukla007/Department-Wise-Digital-Notice-Board_FSD` (`main` branch).
3. Use these settings:
   - **Name:** `department-wise-digital-notice-board-fsd`
   - **Build Command:** *(leave blank)*
   - **Publish Directory:** `.`
4. Click **Create Static Site** — your site will go live at `https://department-wise-digital-notice-board-fsd.onrender.com`.

---

## 👥 Team & Institution

- **Institution:** ABESEC Ghaziabad
- **Developed & Maintained By:**
  - **Ayush Shukla** — Roll No: `2400320100353` (CSE) | GitHub: [@Ayush-Shukla007](https://github.com/Ayush-Shukla007)
  - **Riya Baliyaan** — Roll No: `2400320310143` (ECE)
- **Team:** Full Stack Development Team
- **Project Repository:** [Department-Wise-Digital-Notice-Board_FSD](https://github.com/Ayush-Shukla007/Department-Wise-Digital-Notice-Board_FSD)

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

© 2026 ABESEC Ghaziabad. All Rights Reserved.
