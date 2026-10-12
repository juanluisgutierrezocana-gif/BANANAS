# Banano App

Sistema de control de operaciones para fincas bananeras: recepción de fruta,
inventario de embolse, pérdidas, saldos, orden de calibre, avances agrícolas,
producción y reportería.

## Tecnologías

- React 18 + Vite
- Tailwind CSS + shadcn/ui
- TanStack React Query
- Supabase (PostgreSQL, Auth, RLS)
- Funciones serverless en Vercel (`/api`)
- Pagos con Recurrente (webhook)

## Requisitos

- Node.js 18 o superior
- Un proyecto de Supabase con el esquema de la base de datos

## Instalación local

```bash
npm install
cp .env.example .env.local   # llenar las variables
npm run dev
```

La app queda disponible en `http://localhost:5173`.

## Variables de entorno

| Variable | Dónde se usa |
|---|---|
| `VITE_SUPABASE_URL` | Frontend y funciones `/api` |
| `VITE_SUPABASE_ANON_KEY` | Frontend |
| `VITE_RECURRENTE_PAYMENT_LINK` | Pantalla de suscripción |
| `SUPABASE_SERVICE_ROLE_KEY` | Solo funciones `/api` (servidor) |
| `RECURRENTE_WEBHOOK_SECRET` | Solo `/api/webhooks/recurrente` |

La `SUPABASE_SERVICE_ROLE_KEY` nunca debe exponerse en el frontend.

## Build y despliegue

```bash
npm run build
```

El proyecto está configurado para Vercel (`vercel.json`). Las variables de
entorno se configuran en el panel de Vercel del proyecto.

## Estructura

```
api/            Funciones serverless (registro, alta de usuarios, webhook de pagos)
src/api/        Cliente de Supabase y acceso a tablas
src/components/ Componentes por módulo
src/pages/      Pantallas de la aplicación
src/lib/        Contexto de autenticación, hooks y cálculos
src/utils/      Utilidades (exportación a Excel, etc.)
marketing-site/ Sitio web informativo (HTML estático)
```
