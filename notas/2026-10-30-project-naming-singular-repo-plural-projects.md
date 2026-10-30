# 2026-10-30 — Singular en repositorios, plural en proyectos y namespaces

## Cambios realizados
Se corrige la convención de nombres: el **repositorio** conserva el dominio en singular (`identity-service`); los **proyectos .NET, ensamblados y namespaces base** emplean el plural (`Identities.Spaces`, `Identities.Work`, `Identities.Grounding`, `Identities.Hosting`, y `Identities.Toolkit` solo si se aprueba su creación). Los proyectos de pruebas adoptan `Identities.Tests.Regression`. `Hosting` es la superficie aceptada para ensamblaje; `Toolkit` sigue siendo candidato, no una superficie creada.

## Dónde se aplicaron
- `vslices-solution-architecture/SKILL.md`
- `vslices-capability-architecture/SKILL.md`
- `notas/README.md` (índice)
- La corrección operacional deberá verificarse en `atom-dev-serviu/identity-service`, rama `migration/identity-first-cut`, con sus referencias de proyecto y CI.

## Por qué se hicieron
El repositorio singular no genera conflicto de identificación, pero un namespace/proyecto singular como `Identity.Spaces` puede chocar con un tipo `Identity` del dominio. Es necesario diferenciar el identificador del repositorio de los ensamblados/espacios de código.

## Cómo resuelven el problema
Las Skills instruyen explícitamente a usar plural en proyectos, namespaces base y pruebas, y a comprobar referencias durante renombrados. No se fuerza el cambio de nombres de tipos de dominio singulares ni se materializa `Toolkit` antes de contar con la decisión correspondiente.

## Riesgos reducidos
- Colisiones y ambigüedad de namespaces con tipos del dominio.
- Propagación de nombres singulares a nuevos proyectos, tests y referencias.
- Suposición errónea de que existe un proyecto Toolkit.

## Riesgos aumentados o introducidos
- Los cambios de nombres requieren editar referencias, rutas, tests, CI y documentación en coordinación.
- Los clientes externos pueden depender de namespaces anteriores; deben evaluarse en un corte de migración.
- La pluralización de nombres irregulares exige criterio explícito, no reemplazos mecánicos indiscriminados.

## Estado y verificación
Convención documentada y aplicada a `atom-dev-serviu/identity-service`: renombrados proyectos, namespaces, tests y CI en `migration/identity-first-cut`. Build y pruebas del corte Spaces+Work **verificados en GitHub Actions #41054628503**: 0 errores, 8/8 pruebas exitosas. La prueba real confirma que las nuevas rutas y nombres compilan en este consumidor; no demuestra todavía compatibilidad de todos los consumidores. Esta nota corrige los nombres de proyectos de `2026-10-30-identity-layout-and-dependencies.md` sin reescribir retrospectivamente aquel registro histórico.
