# 🚚 SmartMove - Moving Made Simple

A production-ready React moving service application built with Vite 5 and Tailwind CSS v4. This project demonstrates modern full-stack frontend architecture with authentication, booking systems, and inventory management.

## 📋 Table of Contents

1. [Quick Start](#-quick-start)
2. [Project Structure](#-project-structure)
3. [Complete Setup Guide](#-complete-setup-guide)
4. [Configuration Files](#-configuration-files)
5. [Core Components](#-core-components)
6. [Pages Overview](#-pages-overview)
7. [Styling System](#-styling-system)
8. [Available Scripts](#-available-scripts)
9. [Development Guide](#-development-guide)
10. [Tech Stack](#-tech-stack)

---

## 🚀 Quick Start

### Prerequisites

| Requirement | Minimum Version | Description |
|-------------|-----------------|-------------|
| Node.js | v18.0.0+ | JavaScript runtime |
| npm | v9.0.0+ | Package manager |
| Git | v2.0.0+ | Version control |

### One-Line Installation

```bash
# Clone and set up the entire project
git clone <your-repo-url> && cd smartmove && npm install && npm run dev
```

The development server will start at `http://localhost:5173`

### Build for Production

```bash
npm run build
```

Production files will be generated in the `dist/` directory.

---

## 📁 Project Structure

```
smartmove/
├── .gitignore
├── index.html
├── package.json
├── package-lock.json
├── vite.config.js
├── tailwind.config.js
├── README.md
│
└── src/
    ├── main.jsx                 # Application entry point
    ├── App.jsx                  # Root component & routing
    ├── index.jsx                # Legacy entry (optional)
    ├── style.css                # Global styles & Tailwind imports
    │
    ├── components/
    │   ├── Header.jsx           # Navigation header
    │   └── AuthForm.jsx         # Login/Signup form
    │
    ├── context/
    │   └── AuthContext.jsx      # Authentication state management
    │
    └── pages/
        ├── Home.jsx             # Landing page
        ├── Home.css
        ├── Services.jsx        # Services listing
        ├── Services.css
        ├── About.jsx           # About page
        ├── About.css
        ├── Login.jsx           # User login
        ├── Login.css
        ├── Signup.jsx          # User registration
        ├── Signup.css
        ├── Booking.jsx         # Booking flow
        ├── Booking.css
        ├── Inventory.jsx       # Inventory management
        ├── Inventory.css
        ├── Movers.jsx          # Available movers
        ├── Movers.css
        ├── MyMoves.jsx         # User's move history
        ├── MyMoves.css
        ├── MapView.jsx         # Map visualization
        ├── MapView.css
        ├── Admin.jsx           # Admin dashboard
        └── AdminDashboard.css
```

---

## 📦 Complete Setup Guide

Follow these exact steps to recreate this project from scratch:

### Step 1: Initialize Vite + React Project

```bash
npm create vite@latest smartmove -- --template react
cd smartmove
```

### Step 2: Install Dependencies

```bash
# Core dependencies
npm install react react-dom

# Development dependencies (Tailwind v4 + Vite)
npm install -D @tailwindcss/vite vite autoprefixer
```

### Step 3: Update package.json

```json
{
  "name": "smartmove",
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@tailwindcss/vite": "^4.0.0",
    "autoprefixer": "^10.4.16",
    "postcss": "^8.4.32",
    "vite": "^5.0.10"
  }
}
```

### Step 4: Configure Vite

**File:** `vite.config.js`

```javascript
import { defineConfig } from 'vite'
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [
    tailwindcss(),
  ],
})
```

### Step 5: Configure Tailwind CSS

**File:** `tailwind.config.js`

```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {
      boxShadow: {
        'card': '0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06)',
        'card-hover': '0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05)',
      },
      borderRadius: {
        'card': '1rem',
        'button': '0.5rem',
      }
    },
  },
  plugins: [],
}
```

### Step 6: Set Up HTML Entry Point

**File:** `index.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>SmartMove - Moving Made Simple</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

### Step 7: Create Global Styles

**File:** `src/style.css`

```css
@import "tailwindcss";

@theme {
  --color-app-bg: #f9fafb;
  --color-app-card: #ffffff;
  --color-app-muted: #6b7280;
  --color-app-accent: #4f46e5;
  --color-app-accent-600: #4338ca;
  --font-sans: Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  
  --shadow-card: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
  --shadow-card-hover: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
}

/* Global Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: var(--font-sans);
  background-color: var(--color-app-bg);
  color: #111827;
  line-height: 1.6;
}

/* Component Classes */
@layer components {
  .app-container {
    @apply min-h-screen flex flex-col;
  }

  .card {
    @apply bg-white rounded-2xl border border-gray-100 p-6 transition-all duration-200;
    box-shadow: var(--shadow-card);
  }

  .card:hover {
    box-shadow: var(--shadow-card-hover);
  }

  .btn-primary {
    @apply inline-flex items-center justify-center px-5 py-2.5 rounded-lg bg-indigo-600 text-white font-medium cursor-pointer transition-colors duration-200;
  }

  .btn-primary:hover {
    @apply bg-indigo-700;
  }

  .btn-secondary {
    @apply inline-flex items-center justify-center px-5 py-2.5 rounded-lg border border-gray-200 bg-white text-gray-700 font-medium cursor-pointer transition-colors duration-200;
  }

  .btn-secondary:hover {
    @apply bg-gray-50;
  }

  .input-field {
    @apply block w-full px-4 py-3 rounded-lg border border-gray-200 shadow-sm transition-all duration-200;
  }

  .input-field:focus {
    @apply border-indigo-500 ring-2 ring-indigo-100 outline-none;
  }

  .header {
    @apply sticky top-0 z-50 bg-white/60 backdrop-blur-sm border-b border-gray-200;
  }

  .header-inner {
    @apply max-w-7xl mx-auto px-4 py-4 flex items-center justify-between;
  }

  .navbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;
  }

  .logo-container {
    display: flex;
    align-items: center;
    gap: 10px;
    font-weight: 700;
  }

  .logo-icon {
    width: 36px;
    height: 36px;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    border-radius: 8px;
    background: #111827;
    color: #fff;
  }

  .nav-links {
    display: flex;
    gap: 20px;
    align-items: center;
  }

  @media (max-width: 768px) {
    .nav-links {
      display: none;
    }
  }

  .nav-btn {
    @apply ml-2 px-4 py-2 rounded-lg border-0 bg-transparent cursor-pointer transition-colors text-sm font-medium text-gray-600 hover:text-gray-900;
  }

  .nav-btn.active {
    @apply bg-indigo-600 text-white;
  }

  .nav-link {
    @apply text-sm font-medium text-gray-600 hover:text-gray-900 transition-colors cursor-pointer;
  }

  .container {
    @apply max-w-7xl mx-auto px-4 w-full;
    padding-top: 72px;
  }

  .row {
    @apply flex gap-3 items-center my-4;
  }

  .muted {
    @apply text-gray-500;
  }

  .checkbox {
    @apply w-5 h-5 rounded border-gray-300 text-indigo-600 focus:ring-indigo-500 cursor-pointer;
  }

  .select-field {
    @apply block w-full px-4 py-3 rounded-lg border border-gray-200 shadow-sm bg-white cursor-pointer transition-all duration-200;
  }

  .select-field:focus {
    @apply border-indigo-500 ring-2 ring-indigo-100 outline-none;
  }
}

/* Utility Classes */
.text-gradient {
  @apply bg-clip-text text-transparent bg-gradient-to-r from-indigo-600 to-indigo-400;
}

.section-padding {
  @apply py-16 px-4;
}

.section-title {
  @apply text-3xl font-bold text-gray-900 text-center mb-4;
}

.section-subtitle {
  @apply text-lg text-gray-600 text-center max-w-2xl mx-auto;
}

/* Animations */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fadeIn {
  animation: fadeIn 0.3s ease-out;
}

/* Scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  @apply bg-gray-100;
}

::-webkit-scrollbar-thumb {
  @apply bg-gray-300 rounded-full;
}

::-webkit-scrollbar-thumb:hover {
  @apply bg-gray-400;
}
```

### Step 8: Create Entry Point

**File:** `src/main.jsx`

```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'
import './style.css'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
)
```

### Step 9: Create Root App Component

**File:** `src/App.jsx`

```jsx
import React, { useState } from 'react'
import { AuthProvider } from './context/AuthContext'
import Header from './components/Header'
import Home from './pages/Home'
import Services from './pages/Services'
import About from './pages/About'
import Signup from './pages/Signup'
import MyMoves from './pages/MyMoves'
import Inventory from './pages/Inventory'
import Movers from './pages/Movers'
import Booking from './pages/Booking'
import MapView from './pages/MapView'
import Admin from './pages/Admin'
import Login from './pages/Login'

export default function App() {
  const [page, setPage] = useState('home')
  const [selectedMover, setSelectedMover] = useState(null)

  return (
    <AuthProvider>
      <div className="app">
        <Header onNavigate={setPage} active={page} />
        <main className="container">
          {page === 'home' && <Home onNavigate={setPage} />}
          {page === 'services' && <Services onNavigate={setPage} />}
          {page === 'about' && <About onNavigate={setPage} />}
          {page === 'mymoves' && <MyMoves onNavigate={setPage} />}
          {page === 'inventory' && <Inventory onNavigate={setPage} />}
          {page === 'movers' && <Movers onBook={(m) => { setSelectedMover(m); setPage('booking') }} />}
          {page === 'booking' && (
            <Booking
              onNavigate={setPage}
              selectedMover={selectedMover}
              onConfirm={(details) => {
                alert(`Booking confirmed with ${details.mover?.name || 'N/A'} on ${details.date}`)
                setSelectedMover(null)
                setPage('mymoves')
              }}
            />
          )}
          {page === 'map' && <MapView />}
          {page === 'admin' && <Admin />}
          {page === 'auth' && <Login onSuccess={() => setPage('home')} />}
          {page === 'signup' && <Signup onSuccess={() => setPage('home')} onNavigate={setPage} />}
        </main>
      </div>
    </AuthProvider>
  )
}
```

### Step 10: Create Authentication Context

**File:** `src/context/AuthContext.jsx`

```jsx
import React, { createContext, useContext, useState } from 'react'

const AuthContext = createContext(null)

export function AuthProvider({ children }) {
  const [user, setUser] = useState(null)
  const [isAuthenticated, setIsAuthenticated] = useState(false)

  const login = (email, password) => {
    // Implement actual login logic
    setUser({ email, name: 'Test User' })
    setIsAuthenticated(true)
  }

  const logout = () => {
    setUser(null)
    setIsAuthenticated(false)
  }

  const signup = (name, email, password) => {
    // Implement actual signup logic
    setUser({ name, email })
    setIsAuthenticated(true)
  }

  return (
    <AuthContext.Provider value={{ user, isAuthenticated, login, logout, signup }}>
      {children}
    </AuthContext.Provider>
  )
}

export function useAuth() {
  const context = useContext(AuthContext)
  if (!context) {
    throw new Error('useAuth must be used within an AuthProvider')
  }
  return context
}
```

### Step 11: Create Header Component

**File:** `src/components/Header.jsx`

```jsx
import React from 'react'

export default function Header({ onNavigate, active }) {
  return (
    <header className="header">
      <div className="header-inner">
        <div className="logo-container" onClick={() => onNavigate('home')}>
          <div className="logo-icon">🚚</div>
          <span className="text-xl font-bold">SmartMove</span>
        </div>
        <nav className="nav-links">
          <a className="nav-link" onClick={() => onNavigate('home')}>Home</a>
          <a className="nav-link" onClick={() => onNavigate('services')}>Services</a>
          <a className="nav-link" onClick={() => onNavigate('about')}>About</a>
          <a className="nav-link" onClick={() => onNavigate('mymoves')}>My Moves</a>
          <button className="btn-primary" onClick={() => onNavigate('auth')}>
            Login
          </button>
        </nav>
      </div>
    </header>
  )
}
```

### Step 12: Create Home Page

**File:** `src/pages/Home.jsx`

```jsx
import React from 'react'
import './Home.css'

export default function Home({ onNavigate }) {
  return (
    <div className="home-page">
      {/* Hero Section */}
      <section className="hero-section">
        <h1 className="hero-title">
          Moving Made <span className="text-gradient">Simple</span>
        </h1>
        <p className="hero-subtitle">
          Book professional movers, track your inventory, and manage your move - all in one place.
        </p>
        <div className="hero-buttons">
          <button className="btn-primary" onClick={() => onNavigate('movers')}>
            Book a Move
          </button>
          <button className="btn-secondary" onClick={() => onNavigate('services')}>
            Our Services
          </button>
        </div>
      </section>

      {/* Features Section */}
      <section className="features-grid">
        <div className="card feature-card">
          <h3>📦 Inventory Management</h3>
          <p className="muted">Track and organize all your belongings</p>
        </div>
        <div className="card feature-card">
          <h3>🚚 Professional Movers</h3>
          <p className="muted">Choose from verified moving companies</p>
        </div>
        <div className="card feature-card">
          <h3>📍 Real-time Tracking</h3>
          <p className="muted">Track your move on the map</p>
        </div>
        <div className="card feature-card">
          <h3>📅 Easy Booking</h3>
          <p className="muted">Book in just a few clicks</p>
        </div>
      </section>
    </div>
  )
}
```

**File:** `src/pages/Home.css`

```css
.home-page {
  padding: 2rem 0;
}

.hero-section {
  text-align: center;
  padding: 4rem 2rem;
  margin-bottom: 3rem;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 1.5rem;
  color: #111827;
}

.hero-subtitle {
  font-size: 1.25rem;
  color: #6b7280;
  max-width: 600px;
  margin: 0 auto 2rem;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
}

.feature-card {
  text-align: center;
}

.feature-card h3 {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: #111827;
}
```

### Step 13: Create Additional Pages

Repeat the pattern above for:
- `src/pages/Services.jsx` - List of moving services
- `src/pages/About.jsx` - Company information
- `src/pages/Login.jsx` - User login form
- `src/pages/Signup.jsx` - User registration
- `src/pages/Booking.jsx` - Booking confirmation
- `src/pages/Inventory.jsx` - Inventory list
- `src/pages/Movers.jsx` - Available movers
- `src/pages/MyMoves.jsx` - User's move history
- `src/pages/MapView.jsx` - Interactive map
- `src/pages/Admin.jsx` - Admin dashboard

### Step 14: Create .gitignore

```
# Dependencies
node_modules/

# Build outputs
dist/
build/

# Environment files
.env
.env.local
.env.development.local
.env.test.local
.env.production.local

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Logs
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Testing
coverage/
```

---

## 🔧 Configuration Files

### vite.config.js
Configures Vite with Tailwind CSS v4 plugin.

### tailwind.config.js
Defines custom theme with:
- Custom shadows (`card`, `card-hover`)
- Custom border radius (`card`, `button`)
- Content paths for all components

### src/style.css
Global styles including:
- Tailwind v4 imports
- Custom theme variables
- Reusable component classes
- Animations and transitions
- Scrollbar styling

---

## 🎨 Styling System

### Custom Color Palette

| Variable | Value | Usage |
|----------|-------|-------|
| `--color-app-bg` | `#f9fafb` | Page background |
| `--color-app-card` | `#ffffff` | Card backgrounds |
| `--color-app-muted` | `#6b7280` | Secondary text |
| `--color-app-accent` | `#4f46e5` | Primary actions |
| `--color-app-accent-600` | `#4338ca` | Hover states |

### Component Classes

| Class | Purpose |
|-------|---------|
| `.card` | Main card container |
| `.btn-primary` | Primary CTA button |
| `.btn-secondary` | Secondary button |
| `.input-field` | Form inputs |
| `.header` | Sticky navigation |
| `.container` | Main content wrapper |

---

## 📱 Pages Overview

| Page | Route | Purpose |
|------|-------|---------|
| Home | `home` | Landing page with features |
| Services | `services` | Available services |
| About | `about` | Company info |
| Login | `auth` | User authentication |
| Signup | `signup` | Registration |
| Movers | `movers` | Browse movers |
| Booking | `booking` | Book a mover |
| Inventory | `inventory` | Manage items |
| MyMoves | `mymoves` | View history |
| MapView | `map` | Track moves |
| Admin | `admin` | Dashboard |

---

## 🛠 Development Guide

### Adding a New Page

1. Create `src/pages/NewPage.jsx`:
```jsx
import React from 'react'

export default function NewPage({ onNavigate }) {
  return (
    <div className="new-page">
      <h1>New Page</h1>
    </div>
  )
}
```

2. Add CSS file `src/pages/NewPage.css`

3. Import and add to `App.jsx` routing

### Adding a New Component

1. Create `src/components/NewComponent.jsx`

2. Import where needed:
```jsx
import NewComponent from './components/NewComponent'
```

### Using Tailwind Classes

```jsx
<div className="p-6 bg-white rounded-xl shadow-card hover:shadow-card-hover transition-all">
  Content
</div>
```

---

## 📦 Available Scripts

| Script | Command | Description |
|--------|---------|-------------|
| Dev | `npm run dev` | Start dev server |
| Build | `npm run build` | Production build |
| Preview | `npm run preview` | Preview build |

---

## 🛠 Tech Stack

| Technology | Version | Role |
|------------|---------|------|
| React | 18.2.0 | UI Framework |
| Vite | 5.0.10 | Build Tool |
| Tailwind CSS | 4.0.0 | Styling |
| @tailwindcss/vite | 4.0.0 | Vite Plugin |
| Autoprefixer | 10.4.16 | CSS Processing |

---

## 📄 License

MIT License - Free for personal and commercial use.

---

**Built with ❤️ using React, Vite, and Tailwind CSS v4**

