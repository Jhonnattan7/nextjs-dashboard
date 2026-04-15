# Next.js Dashboard Application

Este es un proyecto *Full-Stack* construido con el **App Router de Next.js**. Es una aplicación web de panel de control (dashboard) que permite gestionar facturas y clientes financieros, demostrando las mejores prácticas del desarrollo moderno en la web.

> **Créditos:** Este proyecto fue desarrollado como culminación del curso oficial [Next.js App Router Course](https://nextjs.org/learn) creado por Vercel, expandiendo sus capacidades para un entorno de producción.

## Características Principales

- **Autenticación Segura:** Implementación de inicio de sesión con credenciales utilizando [NextAuth.js (v5 Beta)](https://nextjs.authjs.dev/). Protegiendo rutas a través de Next.js Middleware.
- **Bases de Datos Relacional:** Conexión a una base de datos PostgreSQL alojada en Neon, operada directamente mediante consultas SQL puras.
- **Mutación de Datos:** Uso nativo de **Server Actions** de React 19 para operaciones CRUD (Crear, Leer, Actualizar, Borrar) y validación de formularios estricta con **Zod**.
- **Búsqueda y Paginación:** Implementación de búsqueda dinámica y paginación guiada a través de parámetros URL (`searchParams`), maximizando el uso de Server Components.
- **Diseño Moderno:** Interfaz de usuario estilizada y accesible construida con **Tailwind CSS**.
- **Manejo de Errores:** Interfaces de fallback con `error.tsx` y `not-found.tsx` para interceptar fallos elegantes.

## Tecnologías (Tech Stack)

- **Framework:** [Next.js](https://nextjs.org/) (App Router)
- **Librería UI:** [React](https://react.dev/)
- **Estilos:** [Tailwind CSS](https://tailwindcss.com/)
- **Base de Datos:** [PostgreSQL](https://www.postgresql.org/) (via [Neon](https://neon.tech/))
- **Autenticación:** [NextAuth.js](https://authjs.dev/)
- **Tipado:** [TypeScript](https://www.typescriptlang.org/)
- **Fuentes e Iconos:** `next/font` (Inter, Lusitana) y Heroicons.

## Arquitectura del Proyecto

El código está estructurado siguiendo el patrón de diseño propuesto por Next.js para el App Router:

- `/app/lib/actions.ts`: Contiene todas las **Server Actions** que mutan datos en la base de datos (crear, editar, eliminar facturas) y disparan la revalidación de caché de Next.js.
- `/app/lib/data.ts`: Capa de lectura de datos que ejecuta peticiones a PostgreSQL para alimentar los Server Components.
- `auth.ts` & `middleware.ts`: Núcleo de autenticación. El *middleware* actúa como un escudo protector interceptando tráfico en las rutas `/dashboard` si el usuario no tiene una sesión activa válida.
- `/app/ui/`: Todos los componentes visuales interactivos y estáticos modulares divididos por contexto (facturas, clientes, panel principal).

## Instalación y Uso Local

Para ejecutar tu propio entorno de desarrollo local, sigue estos pasos:

1. **Clonar e instalar dependencias:**
   Usamos `pnpm` como gestor de paquetes.
   ```bash
   pnpm install
2. **Variables de Entorno**
   POSTGRES_URL="postgresql://usuario:contraseña@servidor.neon.tech/neondb?sslmode=require"
   AUTH_SECRET="tu-clave-secreta-generada"

3. **Inicializar la base de datos (opcional si es tu primera vez)**
  (Asegúrate de entrar a sitio/seed para poblar las tablas con datos y usuarios de prueba)

4. **Correr el servidor**
   pnpm run dev

> **Agradecimientos:** La arquitectura UI/UX inicial y tipologías base provienen de [Next.js by Vercel](https://nextjs.org/learn).
