# 🚗 StarExpress — Landing Page

> Promotional landing page for an automotive repair shop, with an integrated service request form and email notifications — all without an external server.

🌐 **[starexpress.com.mx](https://starexpress.com.mx)**

---

## 📸 Preview

![StarExpress Landing Page](./assets/loading.jpg)

---

## 🎯 About the project

**StarExpress** is an automotive service company with over 40 years of experience. This site was built as a professional landing page with the goal of:

- Showcasing the company's services and philosophy
- Allowing customers to submit service requests
- Automatically sending confirmation emails upon contact
- Being visually appealing, fast, and easy to maintain

### 🧩 The challenge

The client did not want an external server or a complex architecture. The solution was to integrate **everything into a single Astro project**: the landing page, the contact form, and the email system using **Astro's API Routes** together with **Nodemailer** — no separate backend, no database, no additional infrastructure.

---

## 🛠️ Tech stack

| Technology | Usage |
|---|---|
| [Astro 5](https://astro.build/) | Core framework, SSR and API Routes |
| [React 19](https://react.dev/) | Interactive components within Astro |
| [Tailwind CSS 4](https://tailwindcss.com/) | Utility-first styling via Vite plugin |
| [Framer Motion](https://www.framer.com/motion/) | Animations and visual interactions |
| [Zustand](https://zustand-demo.pmnd.rs/) | Global state management for the form |
| [Nodemailer](https://nodemailer.com/) | Email sending from Astro API Route |
| [React Icons](https://react-icons.github.io/react-icons/) | Iconography |
| [TypeScript](https://www.typescriptlang.org/) | Static typing across the project |
| [Netlify](https://www.netlify.com/) | Deploy with official Astro SSR adapter |

---

## 🏗️ Architecture

```
starexpress/
├── src/
│   ├── pages/
│   │   ├── index.astro          # Main landing page
│   │   └── api/
│   │       └── contact.ts       # API Route — email sending with Nodemailer
│   ├── components/
│   │   ├── Hero.astro
│   │   ├── Services.astro
│   │   ├── Gallery.astro
│   │   ├── ContactForm.tsx      # React form with Zustand
│   │   └── ...
│   └── layouts/
│       └── Layout.astro
├── public/
│   └── assets/
├── astro.config.mjs             # Config with Netlify adapter + React + Tailwind
└── package.json
```

### 🔄 Contact form flow

```
User fills out the form
        ↓
React (Zustand) handles local state
        ↓
POST to /api/contact  (Astro API Route)
        ↓
Nodemailer sends confirmation email to the user
        + internal notification to the shop
        ↓
JSON response → UI updates state
```

> The entire flow runs inside the same Astro project deployed on Netlify with SSR. No separate server required.

---

## ✨ Key technical decisions

- **Astro as a lightweight monolith**: Astro's API Routes were used to handle backend logic without a standalone Node.js server.
- **React only where needed**: The rest of the site uses static `.astro` components to maximize performance; React is only used in the interactive form.
- **Tailwind CSS v4 with Vite**: Direct integration via `@tailwindcss/vite` with no separate config file needed.
- **Zustand for the form**: Simple, boilerplate-free state management for fields, validation, and submission status.
- **Framer Motion**: Section entrance animations to enhance the visual experience without hurting performance.

---

## 🚀 Deployment

The site is deployed on **Netlify** using the official `@astrojs/netlify` adapter, which enables the SSR mode required for API Routes to work in production.

---

## 📦 Main dependencies

```json
{
  "astro": "^5.5.6",
  "react": "^19.1.0",
  "tailwindcss": "^4.1.0",
  "framer-motion": "^12.6.3",
  "zustand": "^5.0.3",
  "nodemailer": "^6.10.0",
  "typescript": "^5.8.3"
}
```

---

## 📄 Note

This repository contains only the project documentation. The source code is private by agreement with the client.

---

[starexpress.com.mx](https://starexpress.com.mx)
