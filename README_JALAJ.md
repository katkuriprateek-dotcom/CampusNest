# 🎨 CampusNest — Frontend Developer Tasks
### 👤 Assigned To: Person 2 (Frontend)
### 🛠️ Tech Stack: React.js + Tailwind CSS + Firebase Auth

---

## 📌 Your Role Overview

You are responsible for everything the user **sees and interacts with**.
Your React frontend will connect to the backend APIs built by Person 1 (Node.js/Express).

> ⚠️ **Do NOT touch** the `/backend` folder — that belongs to Person 1.
> Your work lives entirely inside the `/frontend` folder.

---

## 🗂️ Folder Structure You Own

```
/frontend
  /src
    /components        ← Reusable UI pieces (buttons, cards, navbar)
    /pages             ← Full pages (Login, Dashboard, CleaningTracker, etc.)
    /context           ← Auth context (Firebase login state)
    /services          ← API call functions (connect to Person 1's backend)
    /assets            ← Images, icons, logos
  App.jsx              ← Main app with routing
  main.jsx             ← Entry point
```

---

## ✅ Task List

### 🔧 Phase 1 — Setup (Week 1)

- [ ] Install Node.js and create React app using Vite
  ```bash
  npm create vite@latest frontend -- --template react
  cd frontend
  npm install
  ```
- [ ] Install Tailwind CSS
  ```bash
  npm install -D tailwindcss postcss autoprefixer
  npx tailwindcss init -p
  ```
- [ ] Install React Router for navigation
  ```bash
  npm install react-router-dom
  ```
- [ ] Install Axios for API calls
  ```bash
  npm install axios
  ```
- [ ] Set up basic folder structure as shown above
- [ ] Create `.env` file for environment variables (Firebase config, API base URL)
- [ ] Push initial setup to GitHub on branch: `feature/frontend-setup`

---

### 🎨 Phase 2 — UI Design with AI (Week 2)

Use **v0.dev** (v0.dev) to generate your pages. Just describe what you want in plain English and copy the React + Tailwind code it gives you.

**Prompt examples to use on v0.dev:**

```
"A college hostel dashboard with sidebar navigation,
 showing room cleaning status cards, recent complaints,
 and a header with user profile. Use a clean blue and white theme."
```

```
"A login page for a college hostel management app with
 email and password fields, a role selector (Student/Warden/Admin),
 and a submit button. Clean, minimal design."
```

- [ ] Design and build **Login Page** using v0.dev
- [ ] Design and build **Student Dashboard** layout
- [ ] Design and build **Warden Dashboard** layout
- [ ] Design and build **Admin Dashboard** layout
- [ ] Create reusable **Navbar** component
- [ ] Create reusable **Sidebar** component
- [ ] Create reusable **RoomCard** component (shows room no, student name, clean status)
- [ ] Create reusable **IssueCard** component (shows issue type, status badge, date)

---

### 🛏️ Phase 3 — Cleaning Tracker Module (Week 3)

- [ ] **Cleaning Tracker Page** — shows all rooms in a grid/list
  - Each room shows: Room No, Student Name, Last Cleaned Date, Status (✅ / ❌)
  - Filter by: Floor, Block, Date
- [ ] **Mark as Cleaned button** — calls backend API on click
  ```javascript
  // Example API call in /services/cleaningService.js
  export const markRoomCleaned = async (roomId) => {
    const response = await axios.put(`/api/cleaning/${roomId}/mark`);
    return response.data;
  };
  ```
- [ ] **Cleaning History Page** — shows log of past cleanings per room
- [ ] **Warden View** — warden can see all rooms and verify cleaning

---

### ⚡ Phase 4 — Issue Reporting Module (Week 3-4)

- [ ] **Report Issue Form Page**
  - Fields: Issue Type (dropdown), Room No, Description, Photo upload (optional)
  - Issue Types: Electrical ⚡ / Water 💧 / Furniture 🪑 / Internet 📶 / Other
  - Submit button calls backend API
- [ ] **My Issues Page** (Student view)
  - Shows all issues reported by logged-in student
  - Status badge: 🔴 Reported → 🟡 In Progress → 🟢 Resolved
- [ ] **All Issues Page** (Warden/Admin view)
  - Table of all reported issues
  - Filter by: Type, Status, Date, Block
  - Button to update status

---

### 🔐 Phase 5 — Authentication (Week 4, coordinate with Person 3)

- [ ] Connect Firebase Auth to login form
- [ ] Save user role (Student/Warden/Admin) after login
- [ ] Create **Protected Routes** — pages only accessible when logged in
  ```javascript
  // Example ProtectedRoute component
  const ProtectedRoute = ({ children }) => {
    const { user } = useAuth();
    return user ? children : <Navigate to="/login" />;
  };
  ```
- [ ] Redirect to correct dashboard based on role after login
- [ ] Add logout button in navbar

---

### 📊 Phase 6 — Dashboard & Final Polish (Week 5-6)

- [ ] **Student Dashboard** shows:
  - My room cleaning status
  - My reported issues (count + recent ones)
  - Quick "Report Issue" button
- [ ] **Warden Dashboard** shows:
  - Total rooms cleaned today
  - Pending issues count
  - Rooms not cleaned in last 2 days (highlighted in red)
- [ ] **Admin Dashboard** shows:
  - Overall stats (total rooms, total issues, resolved %)
  - Chart of issues by type (use recharts library)
- [ ] Make all pages **mobile responsive** using Tailwind breakpoints
- [ ] Add **loading spinners** when fetching data from API
- [ ] Add **error messages** when API calls fail
- [ ] Final UI review and bug fixes

---

## 🔗 API Endpoints You Will Call
*(Built by Person 1 — confirm these URLs with them)*

| Action | Method | URL |
|--------|--------|-----|
| Get all rooms | GET | `/api/rooms` |
| Mark room cleaned | PUT | `/api/cleaning/:roomId/mark` |
| Get cleaning history | GET | `/api/cleaning/history` |
| Submit issue | POST | `/api/issues` |
| Get my issues | GET | `/api/issues/my` |
| Get all issues | GET | `/api/issues/all` |
| Update issue status | PUT | `/api/issues/:id/status` |
| Login | POST | `/api/auth/login` |

> 💡 Use **Postman** to test these endpoints before connecting them to your React pages.

---

## 📚 Learning Resources

| Topic | Resource |
|-------|----------|
| React basics | "React JS Tutorial - Code With Harry" on YouTube |
| React Hooks | "React Hooks Tutorial - Code With Harry" on YouTube |
| Tailwind CSS | tailwindcss.com/docs (official docs are excellent) |
| React Router | "React Router v6 - Net Ninja" on YouTube |
| Axios API calls | "Axios Crash Course" by Traversy Media on YouTube |
| UI generation | v0.dev — describe your page, get React code |

---

## 🌿 Git Branch Rules

| Branch | Purpose |
|--------|---------|
| `main` | Only working, tested code — do NOT push directly |
| `dev` | Everyone merges here daily |
| `feature/frontend-setup` | Your Phase 1 branch |
| `feature/cleaning-ui` | Your cleaning tracker UI branch |
| `feature/issues-ui` | Your issue reporting UI branch |
| `feature/dashboard` | Your dashboard branch |

**Always:**
```bash
git checkout dev
git pull origin dev          # Get latest before starting work
git checkout -b feature/your-feature-name
# ... do your work ...
git add .
git commit -m "feat: add room cleaning tracker page"
git push origin feature/your-feature-name
# Then open a Pull Request into dev on GitHub
```

---

## 🤝 Coordination Points

- **With Person 1 (Backend):** Confirm API endpoint URLs and response formats before building service files
- **With Person 3 (Auth/DevOps):** Coordinate Firebase setup — they will give you the Firebase config object to put in your `.env` file
- **Daily sync:** Share your screen every 2-3 days to show progress and catch integration issues early

---

## 🏁 Definition of Done

Your frontend work is complete when:
- [ ] All 4 pages are built and connected to real backend APIs
- [ ] Login works with role-based redirects
- [ ] Cleaning tracker marks rooms and shows history
- [ ] Issue reporting form submits and shows status updates
- [ ] Works on mobile screens (responsive)
- [ ] No console errors in the browser
- [ ] Deployed on **Vercel** (free) and accessible via a public URL

---

*CampusNest — Built by students, for students 🏠*
