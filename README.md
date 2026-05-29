# EMUNAH Founders Club

Landing page de captación de leads. Diseñada para convertir visitas en conversaciones de WhatsApp.

**Live:** [emunahfoundersclub.vercel.app](https://emunahfoundersclub.vercel.app)

---

## Stack

- HTML5 + CSS custom properties — sin frameworks, sin dependencias externas
- Google Fonts: Cormorant Garamond + DM Sans
- Deploy: GitHub → Vercel (automático en cada push a `main`)

## Estructura

```
emunahfoundersclub/
├── index.html          ← toda la landing en un solo archivo
└── contexto-master.md  ← documentación del proyecto
```

## Deploy

Cada push a `main` despliega automáticamente en Vercel.

Para deploy manual:
```bash
npx vercel --prod
```

## Pendientes antes de lanzar

- [ ] Reemplazar `57XXXXXXXXXX` con número de WhatsApp real (línea ~756 en `index.html`)
- [ ] Agregar link de presentación virtual
- [ ] Reemplazar testimoniales placeholder con testimoniales reales
- [ ] Agregar logo SVG en `/assets/logo.svg` y actualizar el nav
- [ ] Crear imagen OG `og-image.jpg` (1200×630 px) y descomentar la línea en `<head>`
- [ ] Activar Pixel de Meta para tracking

---

*JOINKOD · Join Media Co. + KODIAK*
