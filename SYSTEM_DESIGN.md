# System Design Document — Department-Wise Digital Notice Board (FSD)

**Institution:** ABESEC Ghaziabad  
**Live Deployment URL:** [https://department-wise-digital-notice-board-fsd.onrender.com](https://department-wise-digital-notice-board-fsd.onrender.com)  
**GitHub Repository:** [Ayush-Shukla007/Department-Wise-Digital-Notice-Board_FSD](https://github.com/Ayush-Shukla007/Department-Wise-Digital-Notice-Board_FSD)  
**Developed & Maintained By:**  
- **Ayush Shukla** — Roll No: `2400320100353` (CSE)  
- **Riya Baliyaan** — Roll No: `2400320310143` (CSE)  
**Team:** Full Stack Development Team  

---

## 1. Purpose & System Overview

The **Department-Wise Digital Notice Board (NoticeHub)** is a single-page web application built for **ABESEC Ghaziabad** to centralize departmental circulars, examination updates, academic calendars, and placement announcements in one searchable, role-aware portal.

### Design Goals
1. **Zero-Backend Static Hosting**: Runs directly in the browser using React 18 and Babel Standalone (`index.html`), deployed on Render Static Site CDN via `render.yaml`.
2. **Departmental Isolation + Central Broadcasts**: Displays notices targeted to a user's registered department alongside common notices (`ALL`) and central institutional cells (`T&P`, `EXAM`), with an optional setting to view all departments.
3. **Client-Side Persistence**: Persists user accounts, active sessions, read/saved notice state, theme preference, and portal settings across reloads using `localStorage` and `sessionStorage`.
4. **Responsive Multi-View Portal**: Provides an authentication split-screen entry point and an 11-view authenticated dashboard with light/dark mode support.

---

## 2. High-Level Architecture

```text
+-------------------------------------------------------------------------+
|                        Browser Client (SPA)                             |
|                                                                         |
|  +--------------------------+       +--------------------------------+  |
|  |   Auth View (App)        | ----> |      Portal Shell (Portal)     |  |
|  |  - Login / Sign Up       |       |  - Sidebar (11 Views)          |  |
|  |  - Dept Chip Selector    |       |  - Topbar (Search, Theme, Bell)|  |
|  |  - Google / Portal SSO   |       |  - NoticeModal & ConfirmDialog |  |
|  |  - ABESEC Header & Footer|       |  - ABESEC Header & SiteFooter  |  |
|  +--------------------------+       +--------------------------------+  |
|               |                                     |                   |
|               v                                     v                   |
|  +-------------------------------------------------------------------+  |
|  |           Browser Storage Layer (storage helper)                  |  |
|  |  - localStorage: nb_users, nb_notices_v1, nb_theme,               |  |
|  |                  nb_userdata_<email>, nb_session (Remember Me)    |  |
|  |  - sessionStorage: nb_session (Session-only login)                |  |
|  +-------------------------------------------------------------------+  |
+-------------------------------------------------------------------------+
                                    ^
                                    | HTTPS (Static CDN Delivery)
                                    v
+-------------------------------------------------------------------------+
|                     Render Static Site (render.yaml)                    |
|  - Source: GitHub main branch                                           |
|  - Publish Directory: . (serves index.html with /* -> /index.html)      |
+-------------------------------------------------------------------------+
```

---

## 3. Technology Stack

| Layer | Technology | Usage in Application |
| :--- | :--- | :--- |
| **UI Framework** | React 18 (`react`, `react-dom` UMD) | Component-based UI, hooks (`useState`, `useEffect`, `useMemo`, `useRef`) |
| **JSX Compiler** | `@babel/standalone` | In-browser transpilation of `<script type="text/babel">` |
| **Styling** | CSS3 + CSS Custom Properties | Split-screen auth layout, responsive grid, `.portal[data-theme="dark"]` |
| **Typography** | Google Fonts (`Plus Jakarta Sans`, `Inter`) | Headings and body text |
| **Graphics** | Inline SVG (`Icon`, department icons) | Zero external icon library dependencies |
| **State & Storage** | `localStorage` & `sessionStorage` | User accounts, sessions, bookmarks, read flags, theme, settings |
| **Hosting** | Render Static Site (`render.yaml`) | Global static CDN serving with SPA fallback rewrite |

---

## 4. Component Architecture

### 4.1 Root & Authentication Flow (`App`)
- Restores an active session on initial render via `restoreSession()`.
- Ensures default **Admin** and **Student** accounts are seeded via `ensureDefaultUsers()`.
- Supports two auth modes (`mode`: `'login' | 'signup'`), department chip pre-selection (`CSE`, `IT`, `ECE`, `ME`, `T&P`, `EXAM`), password visibility toggle, **Remember me** persistence toggle, and one-click SSO demo login (`handleFastSSO`).
- Renders `.auth-shell` containing `.auth-wrapper` (left form panel + right showcase panel) and `<SiteFooter />`.

### 4.2 Portal Shell (`Portal`)
Manages the authenticated workspace across 11 views (`VIEW_META`):

| View ID | Component / Renderer | Purpose |
| :--- | :--- | :--- |
| `dashboard` | `DashboardView` | Welcome banner, 4 KPI cards, Pinned & Important, Announcements, Upcoming Events, Recently Published |
| `all` | `NoticeBrowser` | Full searchable, filterable, sortable list of visible notices |
| `department` | `DepartmentView` | Active department hero card + department switcher chips + filtered feed |
| `academic` | `NoticeBrowser` (locked category) | Academic updates (`Project`, `Assignment`, `Attendance`, `Syllabus`) |
| `exam` | `ExamView` | Two tabs: Examination Notices (`Timetable`, `Result`, `Registration`) and `EXAM_TIMETABLE` table |
| `events` | `EventsView` + `AcademicCalendar` | Three tabs: Upcoming Events, interactive monthly `AcademicCalendar`, and Event Notices |
| `placement` | `PlacementView` | Placement KPI summary + `NoticeBrowser` with `Drive`, `Internship`, `Prep` tag chips |
| `important` | `NoticeBrowser` | Notices filtered by `isImportantNotice` |
| `saved` | `NoticeBrowser` | User-bookmarked notices (`userData.saved`) |
| `profile` | `ProfileView` | Displays user profile details (`name`, `email`, `role`, `department`, `year`, `phone`, `about`) with inline editing |
| `settings` | `SettingsView` | Dark mode, compact cards, high-priority alert toggle, hide expired toggle, show-all-departments toggle, data reset/restore |

### 4.3 Shared UI Components
- **`Sidebar`**: Collapsible responsive navigation grouped into Overview, Categories, Library, and Account, with live unread/saved/important counters and `ABESEC Ghaziabad` branding.
- **`topbar` (`<header>`)**: Mobile drawer toggle, `ABESEC Ghaziabad` badge, live notice search input, theme switcher, notification bell popover (`notifications`), and profile chip.
- **`NoticeCard` & `NoticeRow`**: Displays department badge, relative timestamp, unread dot, priority/status/PDF badges, and quick bookmark/read toggles.
- **`NoticeModal`**: Accessible dialog (`Esc` and backdrop click to close) showing full notice text, metadata grid, attachment download notice, and bookmark/read actions.
- **`ConfirmDialog`**: Confirmation prompt for logout, resetting user read/saved state, and restoring sample notices.
- **`SiteFooter`**: Displays team credits (`Ayush Shukla (2400320100353, CSE) & Riya Baliyaan (2400320310143, CSE)`), `Full Stack Development Team`, and `© 2026 ABESEC Ghaziabad. All Rights Reserved.`.

---

## 5. Data Model & Client Storage Schema

### 5.1 Storage Keys (`STORAGE_KEYS`)

| Key | Store | Value Type | Description |
| :--- | :--- | :--- | :--- |
| `nb_users` | `localStorage` | `User[]` | Registered and seeded user accounts |
| `nb_session` | `localStorage` or `sessionStorage` | `string` (email) | Active logged-in user email (based on `rememberMe`) |
| `nb_notices_v1` | `localStorage` | `Notice[]` | Seeded notices (`buildSeedNotices()`) |
| `nb_theme` | `localStorage` | `'light' \| 'dark'` | Active portal UI theme |
| `nb_userdata_<email>` | `localStorage` | `{ read, saved, settings }` | Per-user read IDs, saved IDs, and portal preferences |

### 5.2 Core Entities

```text
User {
  id: string
  name: string
  email: string
  password: string
  role: "Admin" | "Student"
  department: "CSE" | "IT" | "ECE" | "ME" | "T&P" | "EXAM"
  year: string
  phone: string
  about: string
  createdAt: ISO8601 string
}

Notice {
  id: string
  title: string
  desc: string
  dept: "CSE" | "IT" | "ECE" | "ME" | "T&P" | "EXAM" | "ALL"
  category: "Academic" | "Examination" | "Events" | "Placement" | "General"
  tag: string
  published: ISO8601 string
  deadline: ISO8601 string | null
  eventDate: ISO8601 string | null
  priority: "High" | "Medium" | "Low"
  important: boolean
  pinned: boolean
  attachment: string | null
  postedBy: string
}
```

---

## 6. Authentication & Visibility Logic

### 6.1 Seeded User Roles & Credentials

| Role | Username (Email) | Password | Default Department |
| :--- | :--- | :--- | :--- |
| **Admin** | `admin@abesec.ac.in` | `Admin@123` | `CSE` |
| **Student** | `student@abesec.ac.in` | `Student@123` | `CSE` |
| **Student (Google SSO)** | `student@google.edu` | `password123` | Selected Dept |
| **Student (College Portal SSO)** | `student@portal.edu` | `password123` | Selected Dept |

### 6.2 Validation Rules (`validate()`)
- **Full Name (Sign Up)**: Required, minimum 2 characters, matches `/^[A-Za-z][A-Za-z .'-]+$/`.
- **Email**: Required, validated against `/^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/`.
- **Password**: Required; minimum 6 characters during sign-up.

### 6.3 Notice Visibility & Status Computation
- **Department Visibility Filter**: A notice is visible in the main portal feed when `settings.showAllDepts` is `true`, or `n.dept === user.department`, or `n.dept === 'ALL'`, or `n.dept` is in `CENTRAL_CELLS` (`['T&P', 'EXAM']`).
- **Status Precedence (`getStatus`)**:
  1. `Expired`: `deadline` or `eventDate` is earlier than today (`dayDiff(end) < 0`).
  2. `Important`: `n.important === true` or `n.priority === 'High'`.
  3. `New`: Published within the last 3 days (`< 3 * 86400000` ms).

---

## 7. Deployment Architecture (Render)

Configured via [`render.yaml`](render.yaml):
- **Service Type**: `web` with `runtime: static`
- **Branch**: `main`
- **Build Command**: `""` (no build step required)
- **Publish Directory**: `.`
- **Routing**: Rewrite `/*` → `/index.html`
- **Live URL**: [https://department-wise-digital-notice-board-fsd.onrender.com](https://department-wise-digital-notice-board-fsd.onrender.com)

---

© 2026 ABESEC Ghaziabad. All Rights Reserved.
