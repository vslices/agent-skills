# 2026-10-30 — Estructura explícita de Composition

**Estado:** convención documentada en `main`. No implica que los submódulos o el AppHost ya se hayan creado o ejecutado.

## Cambios realizados
Se incorporó la convención de que una Composition mantiene el **AppHost Aspire en la raíz** y organiza participantes en dos carpetas: `products/` para productos compuestos y `services/` para servicios requeridos por esos productos. En Landing, los participantes previstos son `products/landing-product`, `services/account-service` y `services/identity-service`, como submódulos Git fijados a commits. Aspire referencia los proyectos y recursos necesarios sin adquirir su responsabilidad funcional.

## Dónde se aplicaron
- [Landing Composition — RESPONSIBILITIES.md](https://github.com/atom-dev-serviu/landing-composition/blob/main/RESPONSIBILITIES.md)
- [Solution Architecture — SKILL.md](../vslices-solution-architecture/SKILL.md)
- [Solution Architecture — casos](../vslices-solution-architecture/references/sources-and-cases.md)

## Por qué se hicieron
La Skill indicaba utilizar submódulos y trabajar desde Composition, pero no daba un lugar estable para montarlos ni describía la posición del AppHost. Esto podía generar checkouts diferentes o confundir orquestación con propiedad del código.

## Cómo resuelven el problema
La instrucción fija la estructura de montaje y ofrece al agente una guía verificable al crear la Composition. Distingue organización física del checkout, propiedad de productos/servicios y referencias del AppHost. No impone despliegues independientes por cada submódulo.

## Riesgos reducidos
- Ubicar accidentalmente código de un servicio dentro del AppHost.
- Estructuras de montaje inconsistentes entre composiciones.
- Confundir el orden del árbol con dependencias runtime o propiedad de reglas.
- No poder reconstruir versiones exactas de participantes.

## Riesgos aumentados o introducidos
- Las rutas de proyectos dentro de los submódulos pueden exigir configuración de referencias, compilación y tooling más cuidadosa.
- Dependencias compartidas que hoy están fuera de los tres repositorios requerirán una decisión explícita de incorporación o reutilización.
- Un AppHost raíz puede requerir ajustes frente a las convenciones de plantillas .NET/Aspire; no se asume compatibilidad comprobada.

## Estado y verificación
Las modificaciones documentales fueron publicadas mediante GitHub. No se crearon los submódulos ni el AppHost y no se ejecutaron build ni pruebas E2E. Falta comprobar el montaje real y la resolución de dependencias.
