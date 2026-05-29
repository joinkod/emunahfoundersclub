# JOINKOD — Contexto maestro del proyecto
*Última actualización: 29 mayo 2026*

> **Regla de oro:** NUNCA mencionar Herbalife en ninguna parte visible de ninguno de los proyectos — ni en código, copy, comentarios, meta tags, ni en ningún archivo público.

---

## 1. Contexto del negocio

**Davo** — diseñador gráfico, mercadeo internacional y publicidad, +10 años en branding.
Fundador de **Join Media Co.** Alianza estratégica con **KODIAK** (audiovisual/filmmaking, Renzo Muñoz) = **JOINKOD**.
Distribuidor independiente Herbalife. Colombiano, Pereira.

Filosofía de marca: Mark Hughes — *"Simple, mágico, divertido"*

### Funnel general (ambos proyectos)
```
Ad de Meta → Landing → Botón WhatsApp → Agente IA (n8n + Claude) → Conversión
```
**Un solo número WhatsApp Business** atiende los dos funnels. El agente detecta de cuál landing viene el lead por el mensaje pre-cargado en cada botón.

---

## 2. Proyectos activos

### EMUNAH Founders Club
- **Qué:** Landing funnel de negocio. Capta leads → WhatsApp → presentación Zoom lunes 8pm
- **Conversión:** asistir a la presentación Zoom lunes 8pm hora Colombia
- **Tono:** Premium, sobrio, aspiracional. *"Cree en lo que puedes construir"*
- **Nombre:** Hebreo — fe, confianza, fidelidad (אמונה)
- **Repo GitHub:** `joinkod/emunahfoundersclub`
- **Archivo principal:** `index.html`
- **Deploy:** ✅ Vercel activo — `emunahfoundersclub.vercel.app`

### Sin Remordimientos
- **Qué:** Landing funnel de venta de productos de nutrición. Paquetes 3 niveles + productos individuales + recompra recurrente
- **Conversión:** compra de paquete → recompra mensual
- **Tono:** Vibrante, fresco, apetitoso. *"Vivir sano nunca fue tan rico"*
- **Historia:** Marca preexistente de clubes de nutrición. Logo retro multicolor
- **Paquetes:** Primer Paso / Sin Remordimientos ⭐ / Transformación Total
- **Repo GitHub:** `sinremordimientos`
- **Deploy:** GitHub → Vercel ✅

---

## 3. Infraestructura montada

| Herramienta | Para qué | Estado |
|---|---|---|
| Vercel | Hosting ambas landings | ✅ Activo |
| GitHub | Repositorios de código | ✅ Activo |
| Railway | Servidor n8n self-hosted | ✅ Activo |
| n8n | Automatización agente WhatsApp | ✅ Activo |
| Meta Developers | App "Agente Herbalife 1" creada | ✅ Activo |
| WhatsApp Business | Revisión solicitada a Meta | 🔄 En revisión |
| Claude API | Key creada (nombre: `herbalife-whatsapp`) | ✅ Activo |

### Credenciales clave
- **n8n:** `https://primary-production-34539.up.railway.app` — joinmediaco@gmail.com
- **Railway:** proyecto `resourceful-encouragement` — joinmediaco@gmail.com
- **Claude API:** key guardada en notas personales
- **Meta App:** "Agente Herbalife 1" — davotrading@gmail.com
- **Meta Business Portfolio:** "Emunah Founders Club" — negocio no verificado

### Estado WhatsApp Business
- Dos cuentas Test inhabilitadas desde marzo 2024 (sitio web del perfil no cumplía política comercial de Meta)
- Acción tomada: sitio web actualizado con URL de EMUNAH; revisión solicitada en una de las cuentas
- Pendiente: revisión de la segunda cuenta + aprobación definitiva de Meta

---

## 4. EMUNAH Founders Club — Estado detallado

### Stack
- HTML5 + CSS custom properties + JavaScript vanilla mínimo
- Sin frameworks, sin build steps, sin dependencias externas
- Fuentes Google Fonts: `Cormorant Garamond` (display, 400/600) + `DM Sans` (body, 300/400/500)

### Variables de marca (CSS)
```css
:root {
  --bg:         #f7f7fb;
  --dark:       #0e1428;   /* Azul media noche — fondos oscuros */
  --dark-2:     #141c35;
  --dark-deep:  #080f0a;   /* Footer */
  --gold:       #c97c3a;   /* Ocre suave — acento principal */
  --gold-light: #e8a96a;
  --text:       #14192e;
  --text-muted: #5a607a;
  --white:      #ffffff;
  --surface:    #eeeef8;
  --border:     rgba(0,0,0,0.07);
}
```

### Reglas de diseño — NO romper
1. **Paleta** — solo los colores del `:root`. No introducir colores nuevos sin actualizar este archivo
2. **Herbalife** — NUNCA mencionar en ninguna parte
3. **Tono del copy** — cercano, aspiracional, sin tecnicismos. "Construir ingresos", no "ganar dinero fácil"
4. **CTA principal** — siempre apunta a WhatsApp; nunca a formulario externo
5. **Botones** — `border-radius: 100px` (pill shape)
6. **Imágenes de fondo** — siempre con overlay oscuro para legibilidad
7. **Fuentes** — solo Cormorant Garamond y DM Sans

### Módulos de la landing — estado real

| Módulo | Estado |
|---|---|
| Archivo `index.html` en repo | ✅ Existe |
| Deploy en Vercel | ✅ Activo — `emunahfoundersclub.vercel.app` |
| Nav fijo (logo tipográfico + CTA) | ✅ CSS puro — *no hay carpeta `assets/` ni logo SVG* |
| Hero (pregunta gancho + glows CSS) | ✅ Glows son `radial-gradient` estáticos |
| Pain points (4 cards) | ✅ Implementado |
| La oportunidad (layout 2 col + emblema אמונה) | ✅ Implementado |
| Cómo funciona (3 pasos) | ✅ Implementado |
| Para quién es (6 perfiles) | ✅ Implementado |
| Testimoniales | ✅ Placeholders (MC/Bogotá, JR/Medellín, LP/Cali) |
| CTA final con botón WhatsApp | ✅ Implementado |
| Footer | ✅ Implementado |
| Responsive (≤768px y ≤480px) | ✅ Media queries presentes |
| SEO meta tags + canonical | ✅ Implementado (mayo 2026) |
| Open Graph / Twitter Card | ✅ Implementado — falta og:image |
| Favicon SVG inline | ✅ Implementado (provisional) |
| Scroll reveal (IntersectionObserver) | ✅ Implementado (mayo 2026) |
| Nav sombra al hacer scroll | ✅ Implementado (mayo 2026) |
| Número WhatsApp real | ❌ Sigue como `57XXXXXXXXXX` |
| Link Zoom | ❌ No implementado |
| Testimoniales reales | ❌ Placeholders |
| Pixel de Meta | ❌ No implementado |
| Imagen OG (1200×630 px) | ❌ No creada — línea comentada en `<head>` |
| Logo SVG oficial | ❌ No existe — nav usa texto tipográfico |

---

## 5. Sin Remordimientos — Estado detallado

### Stack
- HTML5 + CSS + JavaScript vanilla
- Fuentes: `Fraunces` (display) + `Outfit` (body)

### Variables de marca (CSS)
```css
/* Paleta — siempre en este orden en gradientes */
--red:    #e51924;
--pink:   #fa777c;
--gold:   #d2b540;
--green:  #a5bd0f;
--teal:   #05a3a4;
```

### Elementos de diseño implementados
- Imágenes de fondo reales (Unsplash) con Ken Burns + overlays
- Badge tornasolado dorado (CSS `@property --shine-angle`)
- Contadores animados, barras de escasez, FAQ acordeón
- Ripple effect en botones, scroll reveal escalonado
- Barra de progreso de lectura, indicador de scroll en hero
- Botón flotante WhatsApp (desktop) + sticky CTA bar (mobile)
- Botón volver arriba

### Pendientes críticos
- [ ] Número WhatsApp real
- [ ] Precios reales en los 3 paquetes
- [ ] Logo SVG
- [ ] Testimoniales reales
- [ ] Link tienda / catálogo

---

## 6. Agente WhatsApp — EMUNAH (n8n) ✅ CONSTRUIDO

### Nodos del flujo
1. **Webhook** — HTTP POST → path: `/whatsapp-emunah`
2. **Code in JavaScript** — extrae: `from`, `messageText`, `contactName`, `messageId`, `phoneNumberId`
3. **IF** — condición: `skip = false` — filtra mensajes válidos vs. status updates
4. **HTTP Request** — llama Claude API con prompt EMUNAH
5. **HTTP Request1** — envía respuesta al cliente vía WhatsApp Cloud API

### Configuración HTTP Request (Claude API)
```
URL:     https://api.anthropic.com/v1/messages
Method:  POST
Headers: x-api-key | anthropic-version: 2023-06-01 | content-type: application/json
Model:   claude-sonnet-4-20250514
Prompt:  Asistente EMUNAH — califica leads, invita al Zoom lunes 8pm, NUNCA menciona Herbalife
```

### Configuración HTTP Request1 (WhatsApp Cloud API)
```
URL:           https://graph.facebook.com/v21.0/{{ $('Code in JavaScript').item.json.phoneNumberId }}/messages
Authorization: Bearer TU_TOKEN_WHATSAPP  ← pendiente reemplazar
Body:          envía $json.content[0].text al número $('Code in JavaScript').item.json.from
```

### Script del agente — Flujo EMUNAH
1. **Bienvenida** automática al primer mensaje
2. **Calificación:** pregunta motivación → disponibilidad lunes 8pm → disposición a actuar
3. **Confirmación** con datos del Zoom
4. **Recordatorios:** mañana del lunes + 1 hora antes

### Estado del agente

| Nodo / Acción | Estado |
|---|---|
| Webhook `/whatsapp-emunah` | ✅ Construido |
| Code (extrae datos del mensaje) | ✅ Construido |
| IF (filtra skip=false) | ✅ Construido |
| HTTP Request → Claude API | ✅ Construido |
| HTTP Request1 → WhatsApp Cloud API | ✅ Construido — token pendiente |
| Token permanente WhatsApp reemplazado | ❌ Pendiente aprobación Meta |
| Webhook registrado en Meta Developers | ❌ Pendiente |
| Flujo publicado (toggle Publish en n8n) | ❌ Pendiente |

### Agente Sin Remordimientos
- ❌ No construido aún

---

## 7. Costos de operación
- Railway (n8n): ~$5/mes
- Meta WhatsApp Cloud API: gratis hasta 1.000 conversaciones/mes
- Claude API: ~$1–3/mes

---

## 8. Pendientes por prioridad

### 🔴 Bloquean el lanzamiento
- [ ] Aprobación Meta WhatsApp Business → token permanente
- [ ] Reemplazar `57XXXXXXXXXX` con número real en `index.html`
- [ ] Agregar link Zoom real en `index.html`
- [ ] Registrar webhook en Meta Developers + publicar flujo en n8n

### 🟡 Mejoran conversión (no bloquean)
- [ ] Logo SVG EMUNAH → reemplazar texto tipográfico en nav
- [ ] Testimoniales reales (ambas landings)
- [ ] Imagen OG 1200×630 px → descomentar línea en `<head>` de `index.html`
- [ ] Pixel de Meta en ambas landings
- [ ] Precios reales en Sin Remordimientos
- [ ] A/B test del copy del hero (EMUNAH)

### ⚪ Futuro (cuando haya tracción)
- [ ] Dominio propio (`emunahfc.com` o `emunah.co`)
- [ ] Página de "gracias" post-conversión
- [ ] Google Analytics / Tag Manager
- [ ] Flujo "Agente Sin Remordimientos" en n8n
- [ ] Segundo funnel con video testimonial en el hero
- [ ] Versión en inglés (EMUNAH)

---

## 9. Referencia de deploy (Vercel)

```bash
# Actualización
npx vercel --prod
```

> `vercel.json` no existe en el repo — Vercel sirve `index.html` automáticamente desde la raíz.

---

## 10. Historial de cambios

| Fecha | Descripción |
|---|---|
| Mayo 2025 | Versión inicial — hero, pain, oportunidad, pasos, perfiles, testimoniales, CTA |
| Mayo 2025 | Paleta actualizada: azul media noche + ocre suave |
| Mayo 2025 | Nombre definido: EMUNAH FOUNDERS CLUB. Agente WhatsApp construido en n8n |
| Mayo 2025 | WhatsApp Business: cuentas test inhabilitadas; revisión solicitada a Meta |
| Mayo 2026 | Verificación CODE: landing confirmada como `index.html`, sin JS. Vercel ✅ activo |
| Mayo 2026 | Fusión de contextos en documento maestro. Contradicciones resueltas |
| Mayo 2026 | `index.html` actualizado: SEO, OG tags, favicon, scroll reveal, nav shadow, © 2026, CSS limpio |
