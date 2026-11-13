# Seguridad y privacidad

- No incluir claves de Cloudflare, tokens GitHub, secretos ni padrones en el repositorio.
- No usar el panel administrativo sin Cloudflare Access correctamente configurado.
- La autorización de una institución debe corresponder a evidencia documental verificable.
- La consulta pública expone únicamente los campos necesarios para comprobar la autenticidad. Evaluar consentimiento y minimización de datos personales conforme a la normativa aplicable.
- Los archivos R2 permanecen privados; descarga administrativa únicamente con sesión autorizada.
- Registrar y revisar acciones de emisión, aprobación y revocación.
- Antes de producción, realizar pruebas de control de acceso multiinstitucional, limitación de peticiones, prevención de abuso y concurrencia.
- Riesgo conocido: la emisión simultánea de una misma inscripción puede generar PDFs temporales; implementar idempotencia transaccional antes de alto volumen.
- Riesgo conocido: la API v1.2 usa un administrador global. Incorporar roles institucionales antes de delegar acceso a terceros.
