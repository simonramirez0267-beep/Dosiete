# dosiete — sitio web

Este repositorio de GitHub es el registro/documentación del proyecto. **El código fuente real y su historial de commits viven en el repositorio Git propio de la plataforma Higgsfield** (donde se construyó, se versiona y se despliega el sitio), porque el pipeline de build/deploy de este proyecto corre sobre esa plataforma, no sobre GitHub Pages/Actions.

## Sitio en vivo

https://dosiete-archive.higgsfield.app

## Qué es

Sitio independiente (sin integración con Higgsfield, sin badges, sin generación de IA en el producto) para dosiete, una casa de curaduría de perfumería con base en Medellín. Construido como una TanStack Start app (React 19, SSR) en un Cloudflare Worker, con D1 como base de datos real (houses/pieces/variants/units/availability/notify_requests/images), panel `/admin` protegido, y el home animado con el motor scroll-scrub (single-shot).

## Estado del build (ver detalle completo en la respuesta del agente)

- Backend D1 completo con las reglas de negocio del spec (archive_number único y nunca reutilizado, campos internos nunca públicos, `Bajo pedido` nunca expone número, `Queda 1` derivado del stock real, verificación por token).
- Las 10 rutas del spec construidas: `/`, `/indice`, `/pieza/[handle]`, `/archive`, `/archive/[numero]`, `/fragments`, `/servicio`, `/legal/*`, `/admin`.
- Las 9 mecánicas de la sección 3.5 del spec implementadas (grano de papel, wordmark que se compone, hairline persistente, contador/odómetro del archivo, banda de registros, disolvencia de material, calibrador, ficha que se registra campo a campo, escala como profundidad).
- **Pendiente de crédito**: el film de scroll-scrub de marca (~15s, dolly continuo sobre materiales, spec §2) requiere 105–180 créditos de generación de video y la cuenta conectada solo tenía 10. El sitio quedó desplegado con un video-placeholder generado sin IA (composición procedural de las mismas texturas minerales, con ffmpeg) para que el mecanismo de scroll-scrub funcione de verdad hoy; queda listo para sustituirlo por el film real en cuanto se aprueben los créditos.
- **ADMIN_PASSWORD**: la herramienta de secretos de la plataforma falló de forma persistente durante esta sesión (bug de la herramienta, no del sitio). La contraseña generada para /admin quedó documentada para que se configure manualmente o en un reintento posterior.

## Brief de diseño completo

Ver `design-brief.md` en este mismo commit.
