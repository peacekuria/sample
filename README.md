# SmartMove - Moving Made Simple

A modern React-based moving service application built with Vite and Tailwind CSS v4. SmartMove provides a seamless platform for customers to book moving services, manage their moves, and track inventory.

## 📁 File Structure

```
smartmove/
├── .gitignore
├── index.html
├── package.json
├── package-lock.json
├── vite.config.js
├── tailwind.config.js
├── postcss.config.js (optional, not present)
├── README.md
└── src/
    ├── main.jsx
    ├── App.jsx
    ├── index.jsx
    ├── style.css
    ├── components/
    │   ├── AuthForm.jsx
    │   └── Header.jsx
    ├── context/
    │   └── AuthContext.jsx
    └── pages/
        ├── Home.jsx
        ├── Home.css
        ├── Services.jsx
        ├── Services.css
        ├── About.jsx
        ├── About.css
        ├── Login.jsx
        ├── Login.css
        ├── Signup.jsx
        ├── Signup.css
        ├── Booking.jsx
        ├── Booking.css
        ├── Inventory.jsx
        ├── Inventory.css
        ├── Movers.jsx
        ├── Movers.css
        ├── MyMoves.jsx
        ├── MyMoves.css
        ├── MapView.jsx
        ├── MapView.css
        └── Admin.jsx
        └── AdminDashboard.css
```

## 🚀 Quick Start

### Prerequisites

- **Node.js** v18 or higher
- **npm** or **yarn** package manager
- Modern web browser (Chrome, Firefox, Safari, Edge)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd smartmove
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```

4. **Open your browser**
   Navigate to `http://localhost:5173` (or the port shown in terminal)

### Build for Production

```bash
npm run build
```

Preview production build:
```bash
npm run preview
```

## ⚙️ Tailwind CSS Setup

This project uses **Tailwind CSS v4** with the `@tailwindcss/vite` plugin.

### Configuration Files

#### `tailwind.config.js`
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

#### `src/style.css`
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

/* Custom component classes */
@layer components {
  .card {
    @apply bg-white rounded-2xl border border-gray-100 p-6 transition-all duration-200;
    box-shadow: var(--shadow-card);
  }
  
  .btn-primary {
    @apply inline-flex items-center justify-center px-5 py-2.5 rounded-lg bg-indigo-600 text-white font-medium cursor-pointer transition-colors duration-200;
  }
  
  .btn-secondary {
    @apply inline-flex items-center justify-center px-5 py-2.5 rounded-lg border border-gray-200 bg-white text-gray-700 font-medium cursor-pointer transition-colors duration-200;
  }
  
  .input-field {
    @apply block w-full px-4 py-3 rounded-lg border border-gray-200 shadow-sm transition-all duration-200;
  }
  
  .header {
    @apply sticky top-0 z-50 bg-white/60 backdrop-blur-sm border-b border-gray-200;
  }
}
```

## ⚡ Vite Configuration

#### `vite.config.js`
```javascript
import { defineConfig } from 'vite'
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [
    tailwindcss(),
  ],
})
```

#### `index.html`
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

## 📦 Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm run preview` | Preview production build |

## 🎨 Design System

### Custom CSS Classes

| Class | Description |
|-------|-------------|
| `.card` | Modern card with shadow and hover effect |
| `.btn-primary` | Primary indigo button |
| `.btn-secondary` | Secondary outlined button |
| `.input-field` | Styled form input |
| `.header` | Sticky header with backdrop blur |
| `.container` | Main container with padding for header |
| `.text-gradient` | Gradient text effect |
| `.animate-fadeIn` | Fade in animation |

### Color Palette

- **Primary**: Indigo (`#4f46e5`)
- **Background**: Light Gray (`#f9fafb`)
- **Card**: White (`#ffffff`)
- **Text**: Dark Gray (`#111827`)

## 📱 Features

### Pages
- **Home** - Landing page with service overview
- **Services** - Available moving services
- **About** - Company information
- **Login/Signup** - User authentication
- **Booking** - Book a moving service
- **Inventory** - Manage moving inventory
- **Movers** - Browse available movers
- **MyMoves** - Track your moves
- **MapView** - Map visualization
- **Admin** - Admin dashboard

### Components
- **Header** - Navigation with mobile support
- **AuthForm** - Authentication form component

### Context
- **AuthContext** - Authentication state management

## 🛠 Technologies

| Technology | Version | Purpose |
|------------|---------|---------|
| React | ^18.2.0 | UI Framework |
| Vite | ^5.0.10 | Build Tool |
| Tailwind CSS | ^4.0.0 | Styling |
| @tailwindcss/vite | ^4.0.0 | Vite Integration |
| Autoprefixer | ^10.4.16 | CSS Post-processing |
| PostCSS | ^8.4.32 | CSS Transformation |

## 🎯 Development Workflow

1. **Create new pages**: Add to `src/pages/` with corresponding CSS
2. **Create new components**: Add to `src/components/`
3. **Add styles**: Use Tailwind classes or extend `style.css`
4. **Run dev server**: `npm run dev`
5. **Build**: `npm run build` before deployment

## 📄 License

MIT License - feel free to use this project for learning and development.

---

Built with ❤️ using React, Vite, and Tailwind CSS

