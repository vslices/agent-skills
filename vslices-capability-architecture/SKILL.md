---
name: vslices-capability-architecture
description: Comprender y aplicar Spaces, Work y Grounding bajo autoridad conceptual de VSlices Framework al desarrollar o revisar capacidades, Features, Points, contratos y realizaciones de servicios VSlices. Usar al implementar comportamiento funcional, definir admisibilidad de valores, solicitar capacidades o verificar garantías; no equiparar estas superficies con Domain, Application e Infrastructure de DDD ni sustituir su definición con una especificación VSIR.
---

# VSlices Capability Architecture

## Autoridad
**Spaces, Work y Grounding son conceptos y superficies organizacionales de VSlices Framework**, sistema de desarrollo que utiliza Language Specification. Consultar [Framework conceptual canónico](https://github.com/the-alive-lab/vslices/blob/main/products/framework/README.md) y [realización de Framework](https://github.com/vslices/framework). Las articulaciones disponibles en [Language Specification](https://github.com/vslices/lang-specification/tree/main/concepts) son fuentes útiles para entender expresión del lenguaje, **no una transferencia de ownership**. La reconciliación exacta entre ambas superficies permanece para revisión específica.

## Criterios que preservar
- **Space:** concepto que establece características y admisibilidad de sus **Points**. **Spaces:** superficie organizacional de esas definiciones; no es un Space superior.
- **Work:** organiza comportamiento, composición funcional, Features y capacidades requeridas. **Feature** no es sinónimo de Work, método, endpoint ni transacción.
- **Grounding:** da realización concreta a capacidades requeridas por Work en condiciones del entorno. No equivale a `Infrastructure`, un repositorio ni un framework.
- **Capability** expresa qué operación puede requerirse/ofrecerse; **Guarantee** expresa propiedades exigibles a una realización en un alcance determinado. Disponibilidad y cumplimiento son afirmaciones diferentes.
- **No imponer una traducción Domain/Application/Infrastructure.** La inspiración DDD no determina estas fronteras; no exigir capas físicas, archivos ni proyectos.
- Una operación pura no requiere necesariamente efectos externos ni Grounding. No inferir atomicidad por secuencia ni durabilidad por seleccionar una base de datos.

## Procedimiento al modificar capacidades
1. Consultar el código, contratos y referencias vigentes de Framework y del servicio consumidor. Distinguir expresamente la definición conceptual, su expresión en Language Specification y el comportamiento observado en una realización; **la relación exacta Framework–Language Specification sigue pendiente de revisión**.
2. Identificar conceptos y Points involucrados, su admisibilidad y qué autoridad define sus condiciones.
3. Describir intención, entrada, salida y promesa de resultado de la Feature sin comenzar por el transporte o la persistencia.
4. Identificar Capabilities solicitadas, Guarantees necesarias y dónde Grounding puede realizarlas; distinguir lo requerido de lo comprobado.
5. Examinar composición, fallos parciales y compatibilidad; realizar cambios mínimos, pruebas apropiadas y documentar la evidencia. Para casos de implementación, contrastar con un ejemplo real de Framework o del servicio; si no hay ejemplo verificable, no convertir un patrón supuesto en convención.
6. Explicar **beneficio → costo → límite** de las decisiones cuando corresponda; señalar preguntas abiertas sin inventar contratos del Framework.

Consultar [significados y contraejemplos](references/semantics-and-rationale.md) cuando la tarea tenga ambigüedad conceptual y [fuentes y casos de evaluación](references/sources-and-cases.md) al trabajar con mecanismos o lenguaje.

## Organización del servicio (convención de consumidor)
En la migración de Identity Service, usar `src/Identity.Spaces`, `src/Identity.Work`, `src/Identity.Grounding` como proyectos que materializan las superficies correspondientes; no derivar de su ubicación contratos conceptuales nuevos. Mantener las dependencias del servicio bajo `dependencies/` (por ahora `TerritorialDivisions` como código directo, no submódulo de Composition). Mantener pruebas actuales en `tests/Identity.Tests.Regression`; `tests/Identity.Tests.Progression` es una intención experimental, **no crearla aún**. El proyecto que expone el servicio mediante API, CLI o procesos background necesita nombre y contrato definitivos; `Identity.Entrypoints` es una propuesta, no una decisión adoptada.

## Límites
No asumir que esta Skill se activa por existir en GitHub: comprobar su instalación y la accesibilidad de fuentes, o declarar la limitación. No declarar que la sintaxis VSIR nueva, Flow, WorkFlow, WorkProcess o WorkStep ya tienen contratos cerrados cuando la fuente no lo demuestre. No convertir una forma observada de la implementación .NET en regla conceptual universal. Mantener separado el diseño de capacidades de la organización Service/Product/Composition: consultar `vslices-solution-architecture` cuando la tarea atraviese esos límites.
