# PURIY CERT v1.2 — PURIYLAB

Plataforma híbrida de credenciales verificables: emisión propia y servicio tecnológico para instituciones autorizadas. Respaldo: Andean Innovation and Technology.

## Incluye
- Portal público responsive de verificación de código y QR.
- Panel visual para organizaciones, eventos, participantes, importación CSV (hasta 100 por lote), inscripciones, validación de elegibilidad y emisión individual.
- API Cloudflare Workers con verificación JWT de Cloudflare Access para endpoints administrativos.
- Base D1 con separación por organización en relaciones críticas, auditoría y estado de revocación.
- R2 privado para PDF, no accesible públicamente.
- Pipeline GitHub Actions de comprobación.

## Antes de emitir certificados reales
1. Autorización institucional explícita, especialmente para UNSCH.
2. Padrón y criterios de elegibilidad aprobados.
3. Revisar y aprobar plantilla PDF y firmas: el PDF actual es **provisional**, no tiene firmas oficiales.
4. Activar Cloudflare Access y probar permisos, CORS, D1 y R2.
5. Revisar riesgos de seguridad y pruebas de carga. No publicar datos reales antes de superar estas verificaciones.

## Instalación
Desde la raíz del repositorio:

```bash
npm install
npm run check
npm run build
```

## Despliegue
Lee `DEPLOYMENT.md`. No se incluyen tokens ni secretos.

## Advertencias conocidas
- La plantilla PDF usa fuentes PDF estándar; ciertos caracteres Unicode en nombres pueden fallar. Antes de emitir, incorporar una fuente Unicode autorizada y pruebas de nombres reales.
- El importador CSV del panel admite únicamente archivos simples sin comas internas en los campos. Validar antes de usarlo en producción.
- La autenticación del panel depende de la política de Cloudflare Access; el frontend por sí solo no autentica.
- No se ha probado en producción ni conectado a la cuenta Cloudflare del usuario.
