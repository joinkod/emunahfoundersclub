# EMUNAH Founders Club — Contexto definitivo del proyecto
*Última actualización: 24 mayo 2026*

> **Regla de oro:** NUNCA mencionar Herbalife en ninguna parte visible del proyecto — ni en código, copy, comentarios, meta tags, ni en ningún archivo.

---

## 1. Stack y Arquitectura actual

### Landing page
- **HTML5 + CSS custom properties + JavaScript vanilla** — sin frameworks, sin build steps, sin dependencias externas
- **Fuentes Google Fonts:** `Cormorant Garamond` (display, pesos 400/600) + `DM Sans` (body, pesos 300/400/500)
- **Deploy:** GitHub → Vercel (hosting estático)
- **Repo:** `emunah-founders-club`

### Variables de marca (CSS)
```css
:root {
  --bg:         #f7f7fb;
  --dark:       #0e1428;   /* Azul media noche — fondos oscuros */
  --dark-2:     #141c35;
  --gold:       #c97c3a;   /* Ocre suave — acento principal */
  --gold-light: #e8a96a;
  --text:       #14192e;
  --text-muted: #5a607a;
  --white:      #ffffff;
  --surface:    #eeeef8;
  --border:     rgba(0,0,0,0.07);
}
```

### Agente WhatsApp (backend)
- **n8n** self-hosted en **Railway** (~$5/mes)
- **Claude API** (`claude-sonnet-4-20250514`) para generación de respuestas
- **Meta WhatsApp Cloud API** (gratis hasta 1.000 conversaciones/mes)
- **Un solo número WhatsApp Business** maneja los dos funnels (EMUNAH + Sin Remordimientos). El agente detecta de cuál landing viene el lead por el mensaje pre-cargado.

### Infraestructura montada
| Herramienta | Para qué | Estado |
|---|---|---|
| Vercel | Hosting landing | ✅ Activo |
| GitHub | Repositorio de código | ✅ Activo |
| Railway | Servidor n8n self-hosted | ✅ Activo |
| n8n | Automatización agente WhatsApp | ✅ Activo |
| Meta Developers | App "Agente Herbalife 1" creada | ✅ Activo |
| WhatsApp Business | Revisión solicitada a Meta | 🔄 En revisión |
| Claude API | Key creada (nombre: herbalife-whatsapp) | ✅ Activo |

### Credenciales clave
- **n8n:** `https://primary-production-34539.up.railway.app` — joinmediaco@gmail.com
- **Meta App:** "Agente Herbalife 1" — davotrading@gmail.com
- **Meta Business Portfolio:** "Emunah Founders Club" — negocio no verificado

---

## 2. Estado del desarrollo

### ⚠️ ADVERTENCIA — Contradicción CODE vs. CHAT
El contexto anterior marcaba la landing como "Primera versión completa ✅", pero el directorio local **no contiene** `emunah-landing.html`, `vercel.json` ni la carpeta `assets/`. El código puede estar en el repositorio remoto de GitHub (`emunah-founders-club`) o pendiente de creación. Verificar antes de continuar.

### Módulos por estado

#### Landing page (`emunah-landing.html`)
| Módulo | Estado real |
|---|---|
| Archivo HTML en repositorio local | ❌ No encontrado en directorio actual |
| Deploy en Vercel | ⚠️ No confirmado — verificar repo remoto |
| Secciones diseñadas (nav, hero, pain, oportunidad, pasos, perfiles, testimoniales, CTA) | 📋 Definidas en documentación |
| Número WhatsApp real (`57XXXXXXXXXX`) | ❌ Pendiente |
| Link Zoom (presentación lunes 8pm Colombia) | ❌ Pendiente |
| Logo SVG de EMUNAH en nav | ❌ Pendiente |
| Testimoniales reales (nombre, ciudad, resultado) | ❌ Pendiente |
| Pixel de Meta | ❌ Pendiente |

#### Agente WhatsApp en n8n
| Nodo | Estado |
|---|---|
| Webhook `/whatsapp-emunah` | ✅ Construido |
| Code (extrae from, messageText, contactName, messageId, phoneNumberId) | ✅ Construido |
| IF (filtra skip=false) | ✅ Construido |
| HTTP Request → Claude API | ✅ Construido |
| HTTP Request1 → WhatsApp Cloud API | ✅ Construido — token pendiente |
| Token permanente WhatsApp reemplazado | ❌ Pendiente aprobación Meta |
| Webhook registrado en Meta Developers | ❌ Pendiente |
| Flujo publicado (toggle Publish) | ❌ Pendiente |

#### Flujo "Agente Sin Remordimientos"
- ❌ No construido aún

---

## 3. Decisiones clave de diseño y negocio

### Funnel completo
```
Ad de Meta → Landing → Botón WhatsApp → Agente IA (n8n + Claude) → Presentación Zoom → Negocio
```
- **Conversión EMUNAH:** asistir a la presentación Zoom lunes 8pm hora Colombia
- **Conversión Sin Remordimientos:** compra de paquete → recompra mensual

### Reglas de diseño — NO romper
1. **Paleta** — Solo los colores en `:root`. No introducir colores nuevos sin actualizar este archivo
2. **Herbalife** — NUNCA mencionar en ninguna parte del proyecto
3. **Tono del copy** — Cercano, aspiracional, sin tecnicismos. "Construir ingresos", no "ganar dinero fácil"
4. **CTA principal** — Siempre apunta a WhatsApp; nunca a formulario externo
5. **Botones** — `border-radius: 100px` (pill shape)
6. **Imágenes de fondo** — Siempre con overlay oscuro encima para legibilidad
7. **Fuentes** — Solo Cormorant Garamond y DM Sans

### Decisiones de arquitectura
- **Vanilla HTML/JS** — elegido deliberadamente para eliminar dependencias y simplificar deploy. No migrar a frameworks sin necesidad real.
- **Un solo número WhatsApp** para ambos funnels — el agente distingue el flujo por el mensaje pre-cargado del botón en cada landing
- **n8n self-hosted en Railway** sobre n8n Cloud — control de costos y datos

### Configuración del agente Claude (HTTP Request en n8n)
```
URL:     https://api.anthropic.com/v1/messages
Method:  POST
Headers: x-api-key | anthropic-version: 2023-06-01 | content-type: application/json
Model:   claude-sonnet-4-20250514
Prompt:  Asistente EMUNAH, califica leads, invita al Zoom lunes 8pm, NUNCA menciona Herbalife
```

### Script del agente WhatsApp — Flujo EMUNAH
1. **Bienvenida** automática al primer mensaje
2. **Calificación:** pregunta motivación → disponibilidad lunes 8pm → disposición a actuar
3. **Confirmación** con datos del Zoom
4. **Recordatorios:** mañana del lunes + 1 hora antes

### Contexto del negocio
- **Quién:** Davo — diseñador gráfico, branding, Join Media Co. / JOINKOD (alianza con KODIAK / Renzo Muñoz, audiovisual)
- **Rol:** Distribuidor independiente Herbalife construyendo su red con funnels digitales
- **Filosofía de marca:** Mark Hughes — "Simple, mágico, divertido". *Emunah* = fe/confianza/fidelidad en hebreo
- **Por qué sin mencionar Herbalife:** El lead debe llegar a la reunión Zoom sin saber que es Herbalife; la revelación ocurre en la presentación

---

## 4. Siguiente paso inmediato

### Paso 1 — Verificar dónde está el código
El directorio local no contiene los archivos de la landing. Antes de cualquier otra acción:
```
¿Existe el repo emunah-founders-club en GitHub?
→ Si sí: clonar localmente y confirmar qué está deployado en Vercel
→ Si no: crear el HTML desde cero con las secciones documentadas en §2
```

### Paso 2 — Desbloquear el agente WhatsApp
Una vez Meta apruebe el número WhatsApp Business:
1. Obtener token permanente en Meta Developers
2. Reemplazar `TU_TOKEN_WHATSAPP` en HTTP Request1 de n8n
3. Registrar URL del webhook en Meta (`/whatsapp-emunah` + token de verificación)
4. Publicar el flujo en n8n

### Paso 3 — Datos reales en la landing
Con el número aprobado, actualizar en `emunah-landing.html`:
- `57XXXXXXXXXX` → número real
- Link del Zoom de presentación
- Testimoniales reales (nombre, ciudad, resultado concreto)

### Pendientes críticos (bloquean lanzamiento)
- [ ] Confirmar ubicación real del código (`emunah-landing.html`)
- [ ] Aprobación Meta WhatsApp Business → token permanente
- [ ] Número WhatsApp real en el HTML
- [ ] Link Zoom real en el HTML
- [ ] Deploy confirmado en Vercel con URL real

### Pendientes importantes (mejoran conversión)
- [ ] Logo SVG de EMUNAH en el nav
- [ ] Testimoniales reales
- [ ] Pixel de Meta para tracking
- [ ] A/B test del copy del hero

### Futuro (cuando haya tracción)
- [ ] Google Analytics / Tag Manager
- [ ] Dominio propio (`emunahfc.com` o `emunah.co`)
- [ ] Página de "gracias" post-conversión
- [ ] Versión en inglés
- [ ] Flujo "Agente Sin Remordimientos" en n8n
- [ ] Segundo funnel con video testimonial en el hero

---

## Deploy en Vercel (referencia)

```bash
# Primera vez
npx vercel
# Project name → emunah-founders-club / Directory → ./ / Override → N

# Actualización
npx vercel --prod
```

```json
// vercel.json
{
  "version": 2,
  "cleanUrls": true,
  "routes": [
    { "src": "/", "dest": "/emunah-landing.html" }
  ]
}
```

---

## Historial de cambios

| Fecha | Descripción |
|---|---|
| Mayo 2025 | Versión inicial documentada — hero, pain, oportunidad, pasos, perfiles, testimoniales, CTA |
| Mayo 2025 | Paleta actualizada: azul media noche + ocre suave |
| Mayo 2025 | Nombre definido: EMUNAH FOUNDERS CLUB. Agente WhatsApp construido en n8n |
| Mayo 2025 | WhatsApp Business: cuentas test inhabilitadas; revisión solicitada a Meta |
| Mayo 2026 | Fusión de contextos — detectada ausencia de archivos de código en directorio local |
