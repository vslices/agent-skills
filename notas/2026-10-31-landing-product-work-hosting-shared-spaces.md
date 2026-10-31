# 2026-10-31 — Product: convergencia en Work, Hosting y Shared.Spaces condicionado

## Cambios realizados
Se revisaron `vslices-solution-architecture` y `vslices-capability-architecture` para expresar el acuerdo arquitectónico de Landing Product: Views, Spaces, Work, Grounding y Hosting; convergencia de BFF/Queries en Work; `Shared.Spaces` por identidad semántica y no por reutilización superficial. Se actualizaron razones y ejemplos de evaluación.

## Dónde se aplicaron
- `vslices-solution-architecture/SKILL.md`
- `vslices-solution-architecture/references/rationale.md`
- `vslices-solution-architecture/references/sources-and-cases.md`
- `vslices-capability-architecture/SKILL.md`
- `vslices-capability-architecture/references/semantics-and-rationale.md`
- `atom-dev-serviu/landing-product/BOOTSTRAP.md` y `RESPONSIBILITIES.md` como fuente operacional del producto.

## Por qué se hicieron
La documentación de 29-10 describía BFF y Queries como proyectos futuros separados; el acuerdo del 31-10 reconoce que **ambos expresan funcionalidades de producto**. Sin corrección, agentes podían recrear la separación histórica o colocar Features simples en Spaces.

## Cómo resuelven el problema
Ambas Skills remiten al bootstrap propietario, separan semántica (Spaces), funcionalidad (Work), realización (Grounding), presentación (Views) y composición desplegable (Hosting), y distinguen el Hosting del producto de la Composition E2E. La extracción de `Shared.Spaces` es condicional a identidad de significado y admisibilidad. Las antiguas rutas son evidencia de migración, no norma de destino.

## Riesgos reducidos
Duplicación de modelos y reglas autoritativas, artificialización de Queries/BFF, despliegues por ensamblado, dependencias compartidas vacías e inferencia de compatibilidad no demostrada.

## Riesgos aumentados o introducidos
`Work` reúne un espectro amplio de Features; es necesario preservar organización interna por escenarios y no convertirlo en un coordinador monolítico. `Spaces` requiere contrastes finos de semántica de representación y de frontera con cultura/UI; `Shared.Spaces` podría introducir acoplamiento si se extrae sin evidencia.

## Estado y verificación
Cambios documentales publicados en los repositorios propietarios y Skills el 2026-10-31. No se migró código de Landing, no se construyeron nuevos proyectos, no se ejecutaron pruebas de producto, ni se validó activación automática de las Skills. Requiere ensayar casos de evaluación en un agente consumidor y contrastar con código vigente antes de reclamar conformidad arquitectónica.
