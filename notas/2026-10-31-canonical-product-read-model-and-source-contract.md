# 2026-10-31 — Fuente canónica de lectura y contrato de fuentes

## Cambios realizados
Se ampliaron las Skills de Solution Architecture y Capability Architecture tras la decisión de Hernán: cada Product puede definir una fuente/modelo canónico de lectura sin custodiar las escrituras de los Services ni imponer una realización física específica. La lectura transversal puede unir fuentes; el mecanismo (SQL, proyección materializada, ORM) se decide con evidencia.

## Dónde se aplicaron
- `vslices-solution-architecture/SKILL.md`
- `vslices-capability-architecture/SKILL.md`
- `atom-dev-serviu/landing-product/BOOTSTRAP.md` y `RESPONSIBILITIES.md`
- `atom-dev-serviu/landing-composition/RESPONSIBILITIES.md`

## Por qué se hicieron
El caso Landing requiere leer datos de Accounts e Identity, cuyos servicios custodían escritura pero no determinan las necesidades de lectura del producto. La compatibilidad estructural de esos datos debe comprobarse con migraciones auténticas, no solo con dobles o tests locales.

## Cómo resuelven el problema
Las Skills separan modelo semántico, Feature y realización de proyección, y distinguen pruebas locales de contratos de fuentes reales y E2E propiedad de Composition. El caso Serviu fija como condición de operabilidad desarrollo/QA/PROD en una sola base SQL Server, sin universalizar esa topología. Propuestas de separación física requieren alerta, impacto y desarrollo compensatorio antes de adopción.

## Riesgos reducidos
Acoplar el modelo canónico a vistas SQL o tablas materializadas por anticipación; hacer que las lecturas de un Product pertenezcan a Services; confundir mocks con compatibilidad real; tratar separación de bases como simple configuración.

## Riesgos introducidos
Las pruebas de migraciones conjuntas implican infraestructura y costo de CI; la base compartida mantiene acoplamiento estructural entre esquemas; la compuerta de Composition necesita especificar orden, versiones y evidencias.

## Estado y verificación
Documentos publicados el 2026-10-31. No se creó ni ejecutó código de lectura, migración o suites de contrato/E2E. Las Skills versionadas en GitHub no acreditan instalación o activación en un agente consumidor.
