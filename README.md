# VSlices Agent Skills

Espacio para desarrollar y evaluar capacidades reutilizables de agentes que trabajan con VSlices. Este repositorio parte como **espacio de investigación y preparación**; no presupone que las Skills descritas ya estén implementadas, validadas o instaladas.

## Dos Skills propuestas

| Skill candidata | Responsabilidad | Caso de uso |
| --- | --- | --- |
| [`vslices-solution-architecture`](vslices-solution-architecture/SKILL.md) | Enseñar y aplicar la organización **Service / Product / Composition**, con su semántica, límites, beneficios, costos y comprobación de integración. | Un agente modifica Landing, Account Service o una Composition y necesita respetar su ownership. |
| [`vslices-capability-architecture`](vslices-capability-architecture/SKILL.md) | Enseñar y aplicar **Spaces / Work / Grounding** a las capacidades internas, comenzando por servicios, sin equipararlos automáticamente con Domain / Application / Infrastructure. | Un agente implementa una capacidad de un servicio y debe preservar sus invariantes, operaciones y realización de efectos. |

Son **dimensiones complementarias**, no sinónimas ni dos niveles obligatorios de todo repositorio. Una tarea de integración puede requerir solo Solution Architecture; una funcionalidad de servicio puede requerir ambas.

## Propósito

Las Skills deben permitir a un agente nuevo comprender **qué decisión arquitectónica existe, por qué existe, qué beneficio busca, qué costo introduce, dónde está la autoridad y cómo actuar frente a un caso no previsto**. No deben convertirse en un conjunto de órdenes descontextualizadas ni en un reemplazo de la evidencia.

La responsabilidad de **definir o cambiar** la arquitectura sigue en sus responsables humanos/organizacionales; una Skill ayuda a comprenderla, aplicarla, detectar tensiones y proponer revisiones, sin declarar decisiones nuevas como aprobadas.

## Procedimiento de construcción

Consultar [procedimiento de desarrollo y evaluación](docs/skill-development-procedure.md). La prioridad es **cobertura semántica probada**, no longitud documental.

## Autoridad conceptual y enrutamiento

La identidad conceptual de Framework y Language Specification se recupera primero desde [the-alive-lab/vslices](https://github.com/the-alive-lab/vslices), que funciona también como **router** hacia [Framework](https://github.com/the-alive-lab/vslices/blob/main/products/framework/README.md), [Language Specification](https://github.com/the-alive-lab/vslices/blob/main/products/lang-specification/README.md) y las superficies especializadas. Las Skills transmiten criterios y facilitan su aplicación; **no son fuentes normativas competidoras**. La terminología operacional vigente es **Composition** (antes Nexo/Nexus); no confundirla con Nexus documental de Docs Standard.

## Fuentes actuales y autoridad

- [Landing Product: responsabilidades](https://github.com/atom-dev-serviu/landing-product/blob/main/RESPONSIBILITIES.md)
- [Account Service: responsabilidades](https://github.com/atom-dev-serviu/account-service/blob/main/RESPONSIBILITIES.md)
- [Identity Service: responsabilidades](https://github.com/atom-dev-serviu/identity-service/blob/main/RESPONSIBILITIES.md)
- [Landing Composition: responsabilidades](https://github.com/atom-dev-serviu/landing-composition/blob/main/RESPONSIBILITIES.md)
- [VSlices Framework](https://github.com/vslices/framework) — estudiar las superficies canónicas de Spaces / Work / Grounding antes de redactar su Skill como normativa.

Los contratos específicos de un repositorio conservan sus responsabilidades concretas. Las Skills no deben copiar todo su contenido; deben orientarse a consultarlos y explicar cómo interpretar los casos reales.

## Registro de cambios

Las mejoras de las Skills y su justificación se registran en [notas/](notas/README.md). Cada nota describe ubicación, motivo, mecanismo de resolución y riesgos reducidos y aumentados; no debe confundir una propuesta con una validación ejecutada.

## Estado

**30-10-2026:** primeros borradores de ambas Skills publicados con referencias y casos de evaluación. **No instaladas ni evaluadas todavía con agentes reales**. Spaces, Work y Grounding pertenecen conceptualmente a VSlices Framework; Language Specification articula su expresión en el lenguaje sin asumir ownership. No adoptar como norma definitiva los nombres de las dimensiones sin contrastarlos con el vocabulario canónico.
