# 2026-10-30 — Límites de evidencia, activación y cooperación de Skills

**Tipo:** fortalecimiento documental de dos Skills existentes. **Estado:** cambios publicados en `main`; evaluación de ejecución todavía pendiente.

## Cambios realizados

- Solution Architecture: separa explícitamente la **compuerta de regresión acordada** de la **infraestructura CI realmente disponible**. Establece cómo registrar verificaciones faltantes sin afirmar aprobación global.
- Ambas Skills: advierten que un archivo en GitHub **no implica instalación, disponibilidad ni activación automática** en agentes consumidores.
- Capability Architecture: exige contrastar ejemplos de implementación con código verificable y diferenciar concepto Framework, articulación Language Specification y realización concreta, preservando la revisión conceptual pendiente.
- Referencias de ambas Skills: incorporan expectativas de evidencia por caso y un escenario compartido que cruza Account Service, Landing Product y Landing Composition.
- README principal: introduce la navegación a estas notas y su finalidad.

## Dónde se aplicaron

- [`vslices-solution-architecture/SKILL.md`](../vslices-solution-architecture/SKILL.md)
- [`vslices-capability-architecture/SKILL.md`](../vslices-capability-architecture/SKILL.md)
- [`vslices-solution-architecture/references/sources-and-cases.md`](../vslices-solution-architecture/references/sources-and-cases.md)
- [`vslices-capability-architecture/references/sources-and-cases.md`](../vslices-capability-architecture/references/sources-and-cases.md)
- [`README.md`](../README.md)
- [`notas/README.md`](README.md): formato y trazabilidad.

## Por qué se hicieron

La revisión de los borradores frente a los cuatro contratos `RESPONSIBILITIES.md` de Serviu identificó tres riesgos relevantes: tomar el objetivo de publicación condicionada por E2E como **mecanismo CI ya implementado**; asumir descubrimiento automático de Skills por existir en GitHub; y derivar convenciones de Space/Work/Grounding sin verificarlas en realizaciones reales. También faltaba un escenario que comprobara cooperación sin mezclar las dos dimensiones arquitectónicas.

## Cómo resuelven el problema

Las instrucciones ahora obligan a distinguir **estado acordado / capacidad operativa verificada / validación pendiente**. El agente debe declarar qué consumidores, pruebas, accesos o mecanismos le faltan; puede ejecutar verificaciones disponibles, pero no usarlas como sustitutos de una compuerta global inexistente. La aplicación de Capability Architecture debe identificar evidencia real antes de ofrecer un ejemplo como norma. El caso combinado proporciona un objetivo concreto para pruebas futuras de coordinación entre Skills.

No se afirma que añadir instrucciones garantice cumplimiento: el resultado debe examinarse en agentes consumidores reales.

## Riesgos reducidos

- Aprobación de despliegues con CI parcial o ficticio.
- Declaraciones infundadas de tests verdes, skills instaladas o compatibilidad comprobada.
- Uso de ejemplos hipotéticos de Framework como contratos normativos.
- Confusión entre propiedad de Service/Product/Composition y semántica interna de Spaces/Work/Grounding.

## Riesgos aumentados o introducidos

- **Sobrecarga documental:** pasos adicionales pueden volver más lenta una tarea trivial; mitigar consultando referencias solo cuando afectan la decisión.
- **Dependencia de acceso:** cuando el agente no puede consultar fuentes remotas, debe reportarlo en vez de inferir; ello puede bloquear soluciones donde antes se improvisaba.
- **Ambigüedad de CI objetivo:** la implementación del agregador sigue pendiente y puede requerir un procedimiento temporal explícito de aprobación humana.
- **Ambigüedad de disparadores:** ninguna prueba todavía acredita que las dos Skills se descubren conjuntamente cuando corresponde.

## Estado y verificación

Los cambios fueron escritos mediante el conector GitHub. **No se ejecutaron evaluaciones con agentes reales, E2E, validación de distribución/instalación ni pruebas de CI**. Falta verificar los archivos publicados y ejecutar la batería de casos prevista. El ownership de Spaces, Work y Grounding es de Framework; la articulación exacta con Language Specification permanece para revisión aparte.
