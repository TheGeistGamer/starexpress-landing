# 🚗 StarExpress — Landing Page

> Landing page promocional para taller mecánico automotriz, con sistema integrado de registro de servicios vía formulario y envío de correos — todo sin servidor externo.

🌐 **[starexpress.com.mx](https://starexpress.com.mx)**

---

## 📸 Vista previa

![StarExpress Landing Page](./assets/loading.jpg)

---

## 🎯 Sobre el proyecto

**StarExpress** es una empresa de servicios automotrices con más de 40 años de experiencia. Este sitio fue desarrollado como una landing page profesional con el objetivo de:

- Presentar los servicios y filosofía de la empresa
- Permitir a los clientes registrar solicitudes de servicio
- Enviar confirmaciones de contacto automáticamente por correo
- Ser atractivo, rápido y fácil de mantener

### 🧩 El reto

El cliente no quería un servidor externo ni una arquitectura compleja. La solución fue integrar **todo en un solo proyecto con Astro**: la landing page, el formulario de contacto y el sistema de envío de correos usando las **API Routes de Astro** junto con **Nodemailer** — sin backend separado, sin base de datos, sin infraestructura adicional.

---

## 🛠️ Stack tecnológico

| Tecnología | Uso |
|---|---|
| [Astro 5](https://astro.build/) | Framework principal, SSR y API Routes |
| [React 19](https://react.dev/) | Componentes interactivos dentro de Astro |
| [Tailwind CSS 4](https://tailwindcss.com/) | Estilos utilitarios vía plugin de Vite |
| [Framer Motion](https://www.framer.com/motion/) | Animaciones e interacciones visuales |
| [Zustand](https://zustand-demo.pmnd.rs/) | Estado global del formulario |
| [Nodemailer](https://nodemailer.com/) | Envío de correos desde API Route de Astro |
| [React Icons](https://react-icons.github.io/react-icons/) | Iconografía |
| [TypeScript](https://www.typescriptlang.org/) | Tipado estático en todo el proyecto |
| [Netlify](https://www.netlify.com/) | Deploy con adaptador SSR oficial de Astro |

---

## 🏗️ Arquitectura

```
starexpress/
├── src/
│   ├── pages/
│   │   ├── index.astro          # Landing page principal
│   │   └── api/
│   │       └── contact.ts       # API Route — envío de correos con Nodemailer
│   ├── components/
│   │   ├── Hero.astro
│   │   ├── Services.astro
│   │   ├── Gallery.astro
│   │   ├── ContactForm.tsx      # Formulario React con Zustand
│   │   └── ...
│   └── layouts/
│       └── Layout.astro
├── public/
│   └── assets/
├── astro.config.mjs             # Config con adaptador Netlify + React + Tailwind
└── package.json
```

### 🔄 Flujo del formulario de contacto

```
Usuario llena formulario
        ↓
React (Zustand) maneja estado local
        ↓
POST a /api/contact  (API Route de Astro)
        ↓
Nodemailer envía correo de confirmación al usuario
        + notificación interna al taller
        ↓
Respuesta JSON → UI actualiza estado
```

> Todo el flujo ocurre dentro del mismo proyecto Astro desplegado en Netlify con SSR. No hay servidor separado.

---

## ✨ Decisiones técnicas destacadas

- **Astro como monolito ligero**: Se aprovecharon las API Routes de Astro para manejar el backend sin necesidad de un servidor Node.js independiente.
- **React solo donde se necesita**: El resto del sitio usa componentes `.astro` estáticos para maximizar performance; React se usa únicamente en el formulario interactivo.
- **Tailwind CSS v4 con Vite**: Integración directa vía `@tailwindcss/vite` sin archivo de configuración separado.
- **Zustand para el formulario**: Estado simple y sin boilerplate para manejar los campos, validación y estado de envío.
- **Framer Motion**: Animaciones de entrada en secciones para mejorar la experiencia visual sin sacrificar rendimiento.

---

## 🚀 Deploy

El sitio está desplegado en **Netlify** utilizando el adaptador oficial `@astrojs/netlify`, que habilita el modo SSR necesario para que las API Routes funcionen en producción.

---

## 📦 Dependencias principales

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

## 📄 Nota

Este repositorio contiene únicamente la documentación del proyecto. El código fuente es privado por acuerdo con el cliente.

---

[starexpress.com.mx](https://starexpress.com.mx)
