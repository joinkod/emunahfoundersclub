# EMUNAH Founders Club — Proyecto independiente

> **Instrucción permanente para Claude Code:**
> Al finalizar cada sesión de trabajo, actualiza este archivo:
> 1. Marca como `[x]` las tareas completadas en la sección **Pendientes**
> 2. Agrega una entrada en **Historial de cambios** con fecha, descripción breve de lo que se hizo
> 3. Actualiza **Estado actual** si algo cambió en la estructura o el stack
> 4. Si se agregaron nuevas decisiones de diseño o reglas, añádelas en **Reglas de diseño**
> Esto mantiene el proyecto documentado y permite retomar el trabajo en cualquier sesión futura sin perder contexto.

---

## ¿Qué es este proyecto?

Landing page de conversión para **EMUNAH Founders Club** — embudo de negocio que captura leads y los lleva a una presentación virtual de oportunidad de ingresos.

**El flujo completo:**
```
Ad de Meta → Landing → Botón WhatsApp → Agente IA → Presentación Zoom → Negocio
```

**Regla de oro:** Nunca mencionar Herbalife en ninguna parte de esta landing — ni en código, copy, comentarios, meta tags ni en ningún archivo del proyecto.

---

## Estado actual

- **Archivo principal:** `emunah-landing.html`
- **Estado:** Primera versión completa ✅
- **Deploy:** Pendiente — sin dominio aún, usar URL de Vercel
- **WhatsApp:** Número pendiente de configurar (`57XXXXXXXXXX`)
- **Logo:** Pendiente — se integrará cuando esté disponible en SVG
- **Zoom link:** Pendiente — presentación lunes 8pm Colombia

---

## Estructura del proyecto

```
emunah-founders-club/
├── CLAUDE.md                  ← Este archivo (mantener actualizado)
├── vercel.json                ← Configuración Vercel
├── emunah-landing.html        ← Landing page principal
└── assets/
    ├── logos/
    │   └── emunah-logo.svg    ← Pendiente
    └── images/                ← Imágenes propias futuras
```

---

## Stack técnico

- HTML5 + CSS custom properties + JavaScript vanilla
- Sin frameworks, sin build steps, sin dependencias
- Google Fonts: `Cormorant Garamond` (display) + `DM Sans` (body)
- Deploy: Vercel estático

---

## Variables de marca

```css
:root {
  --bg:         #f7f7fb;   /* Fondo general */
  --dark:       #0e1428;   /* Azul media noche — fondos oscuros */
  --dark-2:     #141c35;   /* Azul media noche secundario */
  --gold:       #c97c3a;   /* Ocre suave — acento principal */
  --gold-light: #e8a96a;   /* Ocre claro — textos sobre oscuro */
  --text:       #14192e;   /* Texto principal */
  --text-muted: #5a607a;   /* Texto secundario */
  --white:      #ffffff;
  --surface:    #eeeef8;   /* Superficie secciones claras */
  --border:     rgba(0,0,0,0.07);
}
```

**Tipografía:**
- Display: `Cormorant Garamond` — pesos 400, 600 (normal e italic)
- Body: `DM Sans` — pesos 300, 400, 500

**Personalidad visual:** Premium, sobria, con propósito. Azul noche + ocre. Sin ruido visual.

---

## Secciones de la landing (en orden)

1. **Nav fijo** — Logo EMUNAH FOUNDERS CLUB + CTA "Quiero saber más"
2. **Hero** — Pregunta gancho sobre libertad financiera, fondo oscuro con glows
3. **Pain points** — 4 situaciones con las que el visitante se identifica
4. **La oportunidad** — Sin mencionar Herbalife, foco en el resultado
5. **Cómo funciona** — 3 pasos: conversamos → te mostramos todo → tú decides
6. **Para quién es** — 6 perfiles de audiencia universal
7. **Testimoniales** — 3 cards (placeholders por reemplazar)
8. **CTA final** — Botón WhatsApp principal

**Efectos activos:**
- Scroll reveal con IntersectionObserver (`.reveal`, `.delay-1/2/3`)
- Glows animados en hero (radial gradients)
- Nav shadow al hacer scroll
- Hover states en cards y botones

---

## Reglas de diseño — NO romper

1. **Paleta** — Solo los colores definidos en `:root`. No introducir colores nuevos sin actualizar este archivo
2. **Herbalife** — NUNCA mencionar en ninguna parte
3. **Tono del copy** — Cercano, aspiracional, sin tecnicismos. "Construir ingresos" no "ganar dinero fácil"
4. **CTA principal** — Siempre apunta a WhatsApp, nunca a un formulario externo
5. **Botones** — Mantener el estilo `border-radius: 100px` (pill shape)
6. **Imágenes de fondo** — Siempre con overlay oscuro encima para legibilidad
7. **Fuentes** — Solo Cormorant Garamond y DM Sans. No agregar otras sin aprobación

---

## Pendientes

### 🔴 Crítico — bloquea el lanzamiento
- [ ] Reemplazar `57XXXXXXXXXX` con número real de WhatsApp Business
- [ ] Agregar link real de Zoom (presentación lunes 8pm hora Colombia)
- [ ] Deploy inicial en Vercel y obtener URL

### 🟡 Importante — mejora la conversión
- [ ] Integrar logo SVG de EMUNAH en el nav
- [ ] Reemplazar testimoniales placeholder con casos reales (nombre, ciudad, resultado)
- [ ] Agregar Pixel de Meta para tracking de conversiones
- [ ] Revisar y ajustar copy del hero con A/B test

### 🟢 Futuro — cuando haya tracción
- [ ] Google Analytics / Tag Manager
- [ ] Dominio propio (candidatos: `emunahfc.com`, `emunah.co`)
- [ ] Página de "gracias" post-conversión
- [ ] Versión en inglés
- [ ] Conectar agente IA de WhatsApp (n8n + Meta API + Claude)
- [ ] Segundo funnel con video testimonial en el hero

---

## Deploy en Vercel (sin dominio)

```bash
# Primera vez
npx vercel

# Responder:
# Set up and deploy? → Y
# Project name → emunah-founders-club
# Directory → ./
# Override settings? → N

# Obtendrás una URL tipo: emunah-founders-club.vercel.app
# Esa URL es la que usas en tus ads hasta tener dominio propio

# Deploy de actualización
npx vercel --prod
```

**`vercel.json` para este proyecto:**
```json
{
  "version": 2,
  "cleanUrls": true,
  "routes": [
    { "src": "/", "dest": "/emunah-landing.html" }
  ]
}
```

---

## Instalación de Claude Code

```bash
# macOS / Linux (recomendado)
curl -fsSL https://claude.ai/install.sh | bash
source ~/.bashrc

# Windows
iex (irm https://claude.ai/install.ps1)

# Verificar
claude --version
claude doctor
```

**Primera sesión:**
```bash
cd emunah-founders-club
claude
# Autenticarse con cuenta Anthropic via OAuth
```

---

## Historial de cambios

| Fecha | Descripción |
|---|---|
| Mayo 2025 | Versión inicial completa — hero, pain, oportunidad, pasos, perfiles, testimoniales, CTA |
| Mayo 2025 | Paleta actualizada a azul media noche + ocre suave |
| Mayo 2025 | Nombre definido: EMUNAH FOUNDERS CLUB |

---

## Contexto del negocio

**Quién:** Davo — diseñador gráfico, branding, Join Media Co. / JOINKOD (alianza con KODIAK)
**Qué:** Distribuidor independiente Herbalife construyendo su red con funnels digitales
**Por qué esta landing:** Capturar leads anónimos desde ads y convertirlos en asistentes a la presentación del lunes sin que sepan que es Herbalife hasta llegar a la reunión
**Filosofía de marca:** Mark Hughes — "Simple, mágico, divertido". Fe en el proceso (Emunah = fe en hebreo)
