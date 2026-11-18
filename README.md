# 📌 Department-Wise Digital Notice Board (FSD)

[![React](https://img.shields.io/badge/React-18-blue.svg?logo=react)](https://react.dev/)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow.svg?logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![Status](https://img.shields.io/badge/Status-Under%20Development-orange.svg)](#)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A centralized, responsive, and interactive digital notice board web application designed for academic institutions. It enables departments to seamlessly publish, categorize, and display announcements, circulars, and notifications in real time for faculty and students.

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Roadmap & Planned Features](#-roadmap--planned-features)
- [Contributing](#-contributing)
- [Author & Acknowledgments](#-author--acknowledgments)

---

## 🌟 Overview

The **Department-Wise Digital Notice Board** is a Full-Stack Development (FSD) project engineered to modernize campus communication. In colleges and universities, physical notice boards are often cluttered, inefficient, and inaccessible remotely. This web platform provides a clean, role-based, department-filtered digital hub where students and faculty can view verified institutional notices anytime, anywhere.

---

## 🎯 Problem Statement

- **Cluttered Physical Boards**: Notices overlap, get torn, or go unnoticed.
- **Lack of Departmental Categorization**: Students must sift through general circulars to find branch-specific announcements (e.g., CSE vs. Mechanical lab schedules).
- **Delayed Information**: Urgent circulars (exam postponements, placement drives) fail to reach students promptly.
- **Paper Wastage**: High recurring printing and manual labor costs.

---

## 🚀 Key Features

- 🏢 **Department-Wise Segmentation**: Filter notices by Computer Science (CSE), Information Technology (IT), Electronics (ECE), Mechanical (ME), Civil, Management, Examination Cell, and Training & Placement (T&P).
- 🔐 **Role-Based Access Control (RBAC)**:
  - **Admin**: Manage departments, users, approve circulars, and monitor platform logs.
  - **Department Coordinator / Faculty**: Draft, publish, edit, and schedule departmental circulars.
  - **Student / Guest**: Browse, search, filter, and download verified notices.
- ⚡ **Priority Alerts & Urgent Banner**: Highlight critical notifications (exams, placement drives, emergency holidays) at the top of the feed.
- 📺 **Digital Kiosk / TV Display Mode**: Fullscreen optimized view with auto-scrolling tickers designed for smart TVs in campus corridors and departmental lobbies.
- 🔍 **Instant Search & Filtering**: Real-time filtering by department, date range, priority, and keywords.
- 📱 **Responsive & Accessible Design**: Optimized for smart TVs, desktop browsers, tablets, and smartphones.

---

## 🛠️ Tech Stack

### Frontend (Current):
- **React 18** (Standalone CDN setup with Babel transpiler)
- **HTML5** & semantic markup
- **CSS3** & Flexbox / Grid for responsive layouts
- **JavaScript (ES6+)** for asynchronous operations and state management

### Backend & Database (Planned Architecture):
- **Node.js** & **Express.js** (REST API)
- **MongoDB** / **PostgreSQL** for persistent document & user storage
- **JWT (JSON Web Tokens)** / **Bcrypt** for secure authentication and authorization
- **Multer / Cloud Storage** for notice attachment handling (PDF circulars, images)

---

## 📂 Project Structure

```text
Department-Wise-Digital-Notice-Board_FSD/
├── .gitignore              # Files and directories ignored by Git
├── index.html              # Main frontend entry point & React components
├── README.md               # Project documentation and guide
└── ...
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
   - Double-click `index.html` to open it directly in your browser.
   - Or use VS Code with the **Live Server** extension: right-click `index.html` and select **"Open with Live Server"**.

---

## 🔮 Roadmap & Planned Features

- [ ] Complete responsive UI with department switcher sidebar.
- [ ] Implement backend RESTful API endpoints with Node.js and Express.
- [ ] Connect database (MongoDB/Mongoose) for dynamic notice creation and retrieval.
- [ ] Add PDF attachment previews and image download support.
- [ ] Push notifications and email alerts for high-priority circulars.
- [ ] Campus Kiosk mode with auto-refresh and rotating banner.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 👤 Author & Acknowledgments

- **Ayush Shukla**
  - GitHub: [@Ayush-Shukla007](https://github.com/Ayush-Shukla007)
  - Project Repository: [Department-Wise-Digital-Notice-Board_FSD](https://github.com/Ayush-Shukla007/Department-Wise-Digital-Notice-Board_FSD)

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
