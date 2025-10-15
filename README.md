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

## 🏁 Hitos y criterios de “hecho”

### Hito 0 — Setup ✅

* Next + Tailwind funcionando.
* README creado.
* Primer commit.

### Hito 1 — Backend ligero

* `/api/ronda-cita` genera una ronda válida (1 cita + 4 opciones).
* Manejo de errores y revalidación básica.

### Hito 2 — Bucle de juego mínimo

* Pantallas: **Inicio → Pregunta → Resultado**.
* Estados de **cargando**, **correcto/incorrecto**, **fin de partida (10/10)**.

### Hito 3 — Puntuación y persistencia

* Racha, aciertos, precisión.
* `localStorage` para mejor racha y ajustes básicos.

### Hito 4 — Modos

* Clásico / Racha / Reto diario (semilla por fecha).

### Hito 5 — Pulido & Deploy

* UI con Tailwind (accesible, responsive, dark mode).
* SEO + OpenGraph.
* Despliegue en Vercel.
* README “portfolio‑ready” (capturas y enlaces).

---

## 🧪 Calidad

* Estados vacíos y de error bien visibles.
* Accesibilidad: foco, roles `aria`, contraste.
* *(Opcional)* Tests **e2e** con **Playwright**: flujo de una partida clásica y reto diario reproducible.

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

## ☁️ Despliegue (Vercel)

1. Importar el repo en **Vercel** → configurar framework **Next.js**.
2. Variables: **no requeridas** en el MVP.
3. Habilitar “Automatically expose System Environment Variables” (por defecto).
4. Deploy y probar rutas **/inicio**, **/pregunta** y **/api/ronda-cita**.

---

## 🖼️ Capturas (añadir cuando estén)

* `docs/capturas/inicio.png`
* `docs/capturas/pregunta.png`
* `docs/capturas/resultado.png`

---

## 📄 Licencia

**MIT** — usa y adapta libremente, citando autoría si reproduces el proyecto.

---

## 👩‍💻 Autoría

Proyecto didáctico desarrollado paso a paso para portfolio.
