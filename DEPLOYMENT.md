# Despliegue en Cloudflare

1. Subir el contenido de esta carpeta a la raíz del repositorio privado `puriy-cert` de GitHub. Mantener `.github` y `.gitignore`.
2. Instalar Node.js 22+ y ejecutar `npm install`, `npm run check`, `npm run build`.
3. Crear D1 `puriy-cert-db` y R2 privado `puriy-cert-private` desde Cloudflare.
4. Sustituir `REEMPLAZAR_POR_ID_D1` en `api/wrangler.toml` por el identificador real de D1.
5. Ejecutar migración desde `api/`: `npx wrangler d1 migrations apply puriy-cert-db --remote`.
6. Configurar en Worker `ACCESS_TEAM_DOMAIN`, `ACCESS_AUD`, `ADMIN_EMAIL` y restringir con Cloudflare Access la ruta `/api/admin/*` o el dominio de administración. Usar una política de acceso de mínimo privilegio.
7. Ajustar `PUBLIC_VERIFY_BASE` y `CORS_ORIGIN` en `api/wrangler.toml`. El origen CORS debe ser el dominio exacto del portal (sin barra final).
8. Desplegar API: `cd api && npx wrangler deploy`.
9. En Cloudflare Pages, conectar el repositorio GitHub. Root directory: `web`; build command: `npm run build`; output directory: `dist`.
10. Configurar `VITE_API_URL` en Pages con la URL real del Worker y volver a desplegar.
11. Configurar el dominio `certificados.puriylab.com` cuando DNS y SSL estén listos.
12. Probar: health, verificación inexistente (404), acceso admin no autorizado (401), creación de organización, evento, inscripción, emisión autorizada, descarga privada y revocación.

**Nota:** Si el Worker está en un dominio diferente, Cloudflare Access puede requerir configuración adicional para entregar el JWT al Worker. No emitir hasta verificar el flujo de identidad de extremo a extremo.
