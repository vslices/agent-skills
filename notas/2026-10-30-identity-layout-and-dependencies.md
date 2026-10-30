# 2026-10-30 — Dependencias y estructura de Identity Service

## Cambios realizados
Se especificó que Composition declara como submódulos únicamente sus productos y servicios participantes; las dependencias internas son administradas por cada propietario. Para Identity Service se definieron `src/Identity.Spaces`, `src/Identity.Work`, `src/Identity.Grounding`, `tests/Identity.Tests.Regression` y `dependencies/TerritorialDivisions` (código directo inicialmente). `Identity.Entrypoints` se propuso para exposiciones API/CLI/background sin adoptarlo definitivamente. `tests/Identity.Tests.Progression` se registra como intención experimental y **no debe crearse aún**.

## Dónde se aplicaron
- [Solution Architecture](../vslices-solution-architecture/SKILL.md)
- [Capability Architecture](../vslices-capability-architecture/SKILL.md)
- [Identity Service RESPONSIBILITIES](https://github.com/atom-dev-serviu/identity-service/blob/main/RESPONSIBILITIES.md)
- [Landing Composition RESPONSIBILITIES](https://github.com/atom-dev-serviu/landing-composition/blob/main/RESPONSIBILITIES.md)

## Por qué se hicieron
Sin una distinción expresa, el agente podía elevar `TerritorialDivisions` a submódulo de Composition, mezclando dependencias de desarrollo de un participante con integrantes del escenario operacional. Faltaba estructura destino explícita para el servicio.

## Cómo resuelven el problema
Separamos la autoridad sobre participantes (Composition) de la administración de dependencias (servicio/producto propietario) y fijamos la estructura de proyectos y pruebas sin convertir un nombre candidato en contrato aprobado.

## Riesgos reducidos
- Acoplamiento accidental de Composition a dependencias internas.
- Pérdida de trazabilidad de `TerritorialDivisions`.
- Migración mecánica de capas legacy y construcción prematura de `Progression`.

## Riesgos aumentados o introducidos
- Copiar directamente código dependiente aumenta el costo de mantenimiento y posible divergencia con la fuente original.
- Nuevos proyectos requieren verificar referencias, contratos y compilación.
- `Entrypoints` podría quedar demasiado amplio o confundirse con host/transporte; requiere revisión de nomenclatura.

## Estado y verificación
Cambios documentales publicados; todavía no se crearon proyectos ni se migró código. No se realizaron builds ni pruebas. El nombre del proyecto de exposición queda propuesto, no aprobado.
