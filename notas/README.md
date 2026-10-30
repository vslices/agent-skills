# Notas de cambios

Este directorio documenta los cambios **materiales** realizados a Skills, fuentes auxiliares y mecanismos de distribución/evaluación. Las notas conservan **decisión → realización → riesgos**. No equivalen por sí solas a pruebas ejecutadas ni a aprobación normativa.

## Formato obligatorio

Cada nota debe incluir, como mínimo, los siguientes apartados:

1. **Cambios realizados:** describir exactamente qué se modificó; distinguir decisión de implementación y de resultado verificado.
2. **Dónde se aplicaron:** rutas relativas del repositorio y, cuando corresponda, commits o referencias externas.
3. **Por qué se hicieron:** problema observable, evidencia de origen y consecuencias de no resolverlo.
4. **Cómo resuelven el problema:** mecanismo concreto por el cual el cambio altera el comportamiento esperado del agente, indicando sus límites.
5. **Riesgos reducidos:** fallos o interpretaciones menos probables gracias al cambio y por qué.
6. **Riesgos aumentados o introducidos:** costos, nuevas dependencias, ambigüedades o efectos no deseados; escribir «no identificados» solo tras examinar el caso.
7. **Estado y verificación:** qué se verificó efectivamente, qué queda por probar, y qué resultados aún no pueden afirmarse.

La fecha, responsables, referencias y decisiones pendientes se incorporan cuando ayuden a reconstruir la trayectoria. Preferir una nota por conjunto de cambios con una causa común; evitar notas por cada corrección trivial.

## Índice

- [2026-10-30 — Límites de evidencia, activación y cooperación de Skills](2026-10-30-skill-readiness-and-evidence.md)
