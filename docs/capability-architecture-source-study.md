# Estudio de fuentes — Spaces, Work y Grounding

**Fecha:** 2026-10-29. **Estado:** recuperación documental inicial para diseñar `vslices-capability-architecture`; **no es una Skill terminada ni una especificación universal nueva**.

## Autoridad conceptual fijada para el desarrollo de la Skill

**Spaces, Work y Grounding pertenecen a VSlices Framework**, entendido como sistema de desarrollo que utiliza Language Specification. La presencia de articulaciones en `vslices/lang-specification` no transfiere su autoridad. La reconciliación exacta con el lenguaje será revisada por separado; no bloquear por ello la Skill de Framework ni reinterpretar unilateralmente los conceptos de lenguaje.

## Corrección fundamental

Es **incorrecto** equiparar `Spaces / Work / Grounding` con `Domain / Application / Infrastructure`. La organización reconoce inspiración histórica en DDD, pero sus definiciones y fronteras **no coinciden** con esas capas. No reformularlas como equivalencias pedagógicas ni transferir implícitamente propiedades de agregados, repositorios o unidades transaccionales.

## Autoridad y contraste de las tres fuentes

1. **[the-alive-lab/vslices](https://github.com/the-alive-lab/vslices/blob/main/README.md)** es fuente canónica de conceptos de la Suite y sus productos. [Framework conceptual](https://github.com/the-alive-lab/vslices/blob/main/products/framework/README.md) reconoce Space, Work y Grounding como distinciones de realizaciones .NET y advierte que no son taxonomía cerrada. El [patrón Service–Product–Nexus](https://github.com/the-alive-lab/vslices/blob/main/products/framework/service-product-nexus.md) es una propuesta contextual previa: la denominación operacional vigente en este esfuerzo es **Composition**. Su ejemplo PostgreSQL pertenece a otro experimento; **Landing utiliza SQL Server**.
2. **[vslices/lang-specification](https://github.com/vslices/lang-specification)** conserva conceptos aprobados y sus límites como candidatos para expresión en VSIR; no toda definición conceptual es una especificación normativa de sintaxis ni una realización comprobada. Ver [C-021 Spaces](https://github.com/vslices/lang-specification/blob/main/concepts/C-021-spaces.md), [C-002 Space](https://github.com/vslices/lang-specification/blob/main/concepts/C-002-space.md), [C-005 Work](https://github.com/vslices/lang-specification/blob/main/concepts/C-005-work.md), [C-006 Grounding](https://github.com/vslices/lang-specification/blob/main/concepts/C-006-grounding.md) y [C-020 Feature](https://github.com/vslices/lang-specification/blob/main/concepts/C-020-feature.md).
3. **[atom-dev-serviu/documentation](https://github.com/atom-dev-serviu/documentation/blob/main/es/proyectos/ticket-support-reconstruction/orientacion-documental.md)** aporta un contexto aplicado: servicios privados con espacios de valores, Points, transformaciones, Work y Grounding; productos con Views, BFF y Queries. Su experimento de reconstrucción no gobierna las decisiones vigentes para Landing. [Caso System/Module](https://github.com/atom-dev-serviu/documentation/blob/main/es/proyectos/ticket-support-reconstruction/modelo-semantico-system-module-spaces.md) es evidencia situada, no norma universal.

## Definiciones diferenciadas

### Space / Point / Spaces

- **Space:** el tipo que expresa un concepto define condiciones de admisibilidad de Points, características y reglas pertinentes. No es por definición una tabla, un agregado DDD, una clase arbitraria ni una geometría matemática fija.
- **Point:** instancia admisible de ese Space; no trasladar el significado de «entidad DDD» por analogía.
- **Spaces:** superficie organizacional que reúne definiciones de Spaces, características y condiciones semánticas para sus Points. **Spaces no es un Space superior** ni altera automáticamente el ownership de los conceptos reunidos.
- La separación de superficies **no exige** proyectos físicos, paquetes, namespaces o archivos distintos.

### Work / Feature / Capability

- **Work:** responsabilidad y superficie organizacional del comportamiento funcional, su composición y capacidades solicitables.
- **Feature:** unidad semántica identificable orientada a una intención, con contrato mínimo de entrada, salida y promesa de resultado. No es sinónimo de Work, endpoint, método, transacción, agregado, Flow o implementación técnica.
- **Capability:** comportamiento u operación reconocible y solicitada/ofrecida; solicitarla no demuestra su disponibilidad.
- La composición de Features debe examinar entrada admisible, compatibilidad de salida y promesa; el orden de acciones no demuestra atomicidad y el conjunto puede crear obligaciones adicionales.

### Grounding / Guarantee

- **Grounding:** organización de realizaciones concretas de capacidades requeridas por Work frente al entorno de ejecución y garantías aplicables. Puede involucrar persistencia, transporte, memoria, reloj u otros recursos.
- **Guarantee:** propiedad que una realización válida debe satisfacer en cierto alcance. Disponer de una Capability no demuestra su Guarantee.
- No equivale a `Infrastructure`, `Repository`, compilador, Ruleset o tecnología concreta. No toda Feature requiere efectos externos o Grounding.
- No inferir aislamiento, durabilidad, atomicidad ni conformidad por la mera presencia de un proveedor técnico.

## Frontera entre las dos Skills

- `vslices-solution-architecture`: **Service, Product, Composition**; quién posee responsabilidad funcional, quién ofrece experiencia y quién ejecuta/verifica escenarios. Complementar con [contratos de Landing](https://github.com/atom-dev-serviu/landing-composition/blob/main/RESPONSIBILITIES.md).
- `vslices-capability-architecture`: **Spaces, Work, Grounding**; cómo representar definiciones admisibles, comportamientos, capacidades y realizaciones en un contexto dado.
- Las dimensiones son compatibles pero ninguna es un alias de la otra. No está acordado extender automáticamente la organización funcional interna de servicios a **Views o Queries**; investigar desde usos reales.

## Beneficios que la futura Skill debe explicar con alcance honesto

- **Autoridad semántica separada:** usar Points en una Feature no permite redefinir las condiciones del Space.
- **Expresión y realización distinguibles:** Work puede describir lo que se requiere sin atarse a un mecanismo de persistencia o transporte.
- **Garantías examinables:** Grounding debe comprobar propiedades relevantes; no convertir dependencias técnicas en pruebas de corrección.
- **Composición examinable:** compatibilidad entre Features e invariantes de Spaces se pueden estudiar sin reducir todo a una colección de métodos o endpoints.
- **Libertad de mecanismo:** preservar la intención aunque cambien Runtime, lenguaje o tecnología; no prometer portabilidad universal sin evidencia.

Costos y riesgos: mayor vocabulario que aprender; necesidad de contratos claros; tentación de duplicar taxonomías o introducir abstracciones no probadas; posible distancia entre definición conceptual y la implementación .NET vigente. Explicar el criterio desde casos reales y reconocer cuestiones todavía abiertas.

## Casos de evaluación que debemos construir después

1. Un agente pretende convertir todo Space en AggregateRoot: debe rechazar la equivalencia.
2. Una Feature utiliza un Point con precondiciones: debe preservar reglas del Space en lugar de redefinirlas.
3. Una operación puramente funcional sin efecto externo: no inventar Grounding.
4. Una implementación de SQL satisface una Capability pero no demuestra durabilidad/aislamiento: distinguir Guarantee y evidencia.
5. Una petición de feature en Landing: invocar arquitectura de solución y, solo cuando corresponda, arquitectura de capacidades.
6. Una sugerencia de mover todas las Queries del producto al servicio: reconocer la autoridad representacional del producto y el límite de extrapolación.
7. Un caso con vocabulario Flow, WorkFlow, WorkProcess o WorkStep: examinar contratos específicos, **no tratarlos como sinónimos**.

## Preguntas abiertas

- Recuperar contratos actuales de Capability/Guarantee y diferencias entre Flow, WorkFlow, WorkProcess y WorkStep.
- Contrastar expresiones concretas de Framework contra estas definiciones, sin elevar implementaciones a norma.
- Definir disparadores y pruebas reales para la Skill y evaluarla con/sin activación.
- Determinar cómo evolucionan las referencias cuando cambian los conceptos aprobados sin copiar definiciones competidoras.

**Procedencia:** esta nota resume las fuentes indicadas y separa definiciones leídas de inferencias sobre beneficios y pruebas futuras. No acredita validación ejecutada de ninguna implementación.
