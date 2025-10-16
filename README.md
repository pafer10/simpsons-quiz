# 🧠 Quiz de Citas — The Simpsons Edition

Aplicación tipo **quiz**: se muestra una cita y el jugador debe adivinar qué personaje la dijo. Construida con **Next.js (App Router)**, **React** y **Tailwind CSS**, consumiendo la API pública de *The Simpsons* a través de un backend ligero en Next (route handler) que normaliza y cachea datos.

---

## 🎯 Objetivo de aprendizaje

Practicar **Full‑stack con Next.js** (SSR/ISR, route handlers), **estado en React**, **UI responsive con Tailwind** y **despliegue en Vercel**.

---

## 🚀 MVP (alcance inicial, sin BD)

**Modo Clásico**

* 10 preguntas por partida.
* Cada ronda: **1 cita real + 4 opciones** (1 correcta, 3 distractores).
* Estados: **cargando**, **correcto/incorrecto**, **fin de partida**.
* Puntuación básica y **mejor racha** persistida en `localStorage`.
* **UI responsive** con **modo claro/oscuro**.

---

## 🌱 Extras (siguientes iteraciones)

* ♾️ **Racha infinita** (termina al primer fallo).
* ⏱️ **Contrarreloj** (X segundos por pregunta).
* 👤 **Pack por personaje** (filtrar por personaje).
* 📅 **Reto diario** (semilla por fecha ⇒ el mismo para todos).
* 📤 **Compartir resultado** (OpenGraph/SEO).
* 🏆 **Ranking global** (añadir BD) — post‑MVP.

---

## 🧩 Tecnologías

* **Next.js** — App Router, Server/Client Components, Route Handlers.
* **React** — Estado y UI.
* **Tailwind CSS** — Diseño, dark mode, responsive.
* **TypeScript**.
* **TheSimpsonsAPI** — vía proxy `/api/ronda-cita`.

---

## 🗂️ Estructura de carpetas (inicial)

```
app/
  (juego)/
    inicio/page.tsx
    pregunta/page.tsx
  api/
    ronda-cita/route.ts
components/
  BotonRespuesta.tsx
  TarjetaCita.tsx
  Encabezado.tsx
lib/
  cliente-api.ts
  tipos.ts
styles/
  globals.css
```

> **Nota:** Nombres y rutas en castellano para coherencia (componentes, páginas y endpoints).

---

## 🔌 Contrato del endpoint interno

### `GET /api/ronda-cita`

#### ✅ Respuesta 200

```json
{
  "cita": {
    "texto": "I, for one, welcome our new insect overlords.",
    "personaje": "Kent Brockman",
    "imagen": "https://.../kent.png"
  },
  "opciones": ["Homer Simpson", "Marge Simpson", "Kent Brockman", "Lisa Simpson"],
  "correcta": "Kent Brockman",
  "semilla": "2025-10-15T00:00:00Z"
}
```

#### ⚠️ Errores

* `502` — Falla la API externa.
* `504` — Tiempo de respuesta excedido.
* `503` — Rate limit superado (sugerir reintento).

#### 🗃️ Cache

* Revalidación simple (p. ej. `export const revalidate = 60`) para aliviar llamadas a la API.

---

## 🖥️ Scripts (pnpm)

```bash
pnpm dev       # entorno local
pnpm build     # build de producción
pnpm start     # servir build
pnpm lint      # linting
```

---

## ▶️ Desarrollo local

1. Clonar el repo y entrar a la carpeta.
2. Instalar dependencias: `pnpm i`.
3. Arrancar: `pnpm dev` y abrir [http://localhost:3000](http://localhost:3000).

---

## 🖼️ Capturas

* `docs/capturas/inicio.png`
* `docs/capturas/pregunta.png`
* `docs/capturas/resultado.png`

---
