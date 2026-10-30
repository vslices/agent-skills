# Fuentes y casos iniciales

## Autoridad
- [Framework — arquitectura de solución](https://github.com/the-alive-lab/vslices/blob/main/products/framework/service-product-nexus.md).
- [Landing Product](https://github.com/atom-dev-serviu/landing-product/blob/main/RESPONSIBILITIES.md).
- [Account Service](https://github.com/atom-dev-serviu/account-service/blob/main/RESPONSIBILITIES.md).
- [Identity Service](https://github.com/atom-dev-serviu/identity-service/blob/main/RESPONSIBILITIES.md).
- [Landing Composition](https://github.com/atom-dev-serviu/landing-composition/blob/main/RESPONSIBILITIES.md).
- [Procedimiento de evaluación](https://github.com/vslices/agent-skills/blob/main/docs/skill-development-procedure.md).

## Casos para evaluar activación y comportamiento
1. Cambio de contraseña solicitado desde Landing: reglas de credencial en Accounts y experiencia en Landing.
2. Portal de aplicaciones accesibles: vista en Landing; no inventar permisos en UI.
3. Account Service pasa pruebas unitarias, falla E2E Landing: bloquear aprobación de versión.
4. Agregar componente a Composition: registrar gitlink, ejecutar escenario, no mover reglas de dominio.
5. Perfil consulta datos de dos servicios: no inferir automáticamente traslado a uno de ellos.
6. Sistema ajeno a VSlices: no aplicar obligatoriamente estas convenciones.

**Escenario combinado pendiente de prueba:** implementar una capacidad de Accounts utilizada por Landing, identificar reglas propietarias, contratos de producto y regresiones de Landing Composition, consultando Capability Architecture únicamente para semántica interna de Spaces/Work/Grounding.

Estos casos son **batería propuesta**, no evaluaciones ya ejecutadas. Para cada ejecución registrar entrada, fuentes efectivamente consultadas, respuesta/cambio producido, evidencia de pruebas y desviaciones. La publicación de los documentos no es prueba de activación ni corrección.
