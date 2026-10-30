---
name: vslices-solution-architecture
description: Aplicar y explicar la arquitectura Service, Product y Composition de VSlices en desarrollo, revisión, pruebas, migración o integración de código en Serviu y otros consumidores de VSlices. Usar al decidir dónde corresponde una responsabilidad funcional, una experiencia de producto o una regresión transversal, al modificar sus contratos o al coordinar cambios entre repositorios; no utilizar para imponer este patrón en sistemas ajenos a VSlices.
---

# VSlices Solution Architecture

## Autoridad y alcance
- Consultar [la definición conceptual del patrón](https://github.com/the-alive-lab/vslices/blob/main/products/framework/service-product-nexus.md). **Composition** es el nombre operacional vigente de la antigua Nexo/Nexus; no confundir con Nexus documental de Docs Standard.
- Consultar siempre el `RESPONSIBILITIES.md` del repositorio afectado. Las decisiones específicas vigentes prevalecen sobre ejemplos históricos. Para Landing, usar SQL Server.
- Actuar dentro de la arquitectura aprobada; identificar tensiones y proponer revisiones, pero no atribuirse autoridad para redefinir ownership.

## Modelo que aplicar
- **Service:** propietario de una responsabilidad funcional, reglas, garantías y estado pertinente; expone capacidades privadas a productos autorizados. No implica despliegue ni base de datos por sí mismo.
- **Product:** propietario de experiencia y procesos propios. En el caso Serviu, Views presenta interacción; BFF coordina procesos y capacidades; Queries conserva modelos de lectura/representación específicos del producto. No duplicar reglas que pertenecen a servicios.
- **Composition:** escenario operacional reproducible de productos, servicios y recursos, **principal superficie de desarrollo integrado y supervisión de regresión**. No posee las reglas funcionales de los participantes. Comprobar los contratos de integración, no solo la disponibilidad del host.
- Distinguir propiedad semántica, repositorio, ensamblado, proceso y despliegue. No inferir microservicios universales.

## Cómo trabajar
1. Identificar el propósito de la modificación y qué participante tiene autoridad sobre las reglas, la experiencia y la verificación.
2. Leer contratos vigentes y evidencia de código; distinguir decisión aprobada, realización observada y propuesta.
3. Modificar el repositorio propietario. Para trabajo transversal, operar preferentemente desde Composition con Git submodules y usar ramas homónimas solo en módulos modificados; fijar versiones mediante gitlinks.
4. Conservar pruebas locales e integración. Ejecutar la matriz E2E de la Composition sobre commits concretos cuando sea técnicamente posible; registrar la evidencia o declarar claramente lo no ejecutado.
5. Para servicio compartido, identificar todas las composiciones consumidoras afectadas y exigir sus pruebas antes de aprobar publicación. **Este es el contrato objetivo, no evidencia de que exista ya el pipeline agregador**. Si la compuerta no está implementada, ejecutar lo verificable, registrar consumidores y verificaciones faltantes y señalar explícitamente que no hay aprobación global. Ninguna Composition aprueba globalmente el servicio por sí sola; el pipeline propietario deberá consolidar resultados. Estados fallidos, omitidos, cancelados, pendientes o desconocidos no aprueban.
6. Explicar decisiones relevantes mediante **responsabilidad → beneficio esperado → costo o riesgo → evidencia** sin dar discursos innecesarios en tareas simples.

Antes de ejecutar una tarea, verificar que esta Skill esté realmente disponible en el entorno; el archivo en GitHub no implica instalación ni descubrimiento automático. Cuando falten conectores o acceso a fuentes, declarar la limitación sin reconstruir contratos de memoria.

Consultar [razones y contraejemplos](references/rationale.md) cuando surja un caso ambiguo. Consultar [fuentes y casos de prueba](references/sources-and-cases.md) para cambios multi-repositorio y evaluación.

## Límites
- No trasladar automáticamente PostgreSQL, topologías HTTP u otras decisiones de experimentos de Ticket Support al esfuerzo Landing.
- No confundir un servicio con una API, un producto con una pantalla ni una Composition con un simple AppHost.
- No inventar compatibilidad comprobada, CI verde o publicación completada. Diferenciar remota, candidata, evaluada, adoptada y desplegada.
- Si la tarea requiere semántica interna de Spaces, Work o Grounding, consultar `vslices-capability-architecture` sin equipararla a capas DDD.
