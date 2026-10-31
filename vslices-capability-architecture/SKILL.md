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

## Aplicación a Products: acuerdo Landing (2026-10-31)

- **Spaces define espacios; Work define funcionalidades; Grounding realiza capacidades.** Esta separación también vale para Product sin duplicar capas innecesarias ni traducirla rígidamente a DDD.
- En [Landing Product](https://github.com/atom-dev-serviu/landing-product/blob/main/BOOTSTRAP.md), tanto las Features históricas de `Landing.BFF` como las de `Landing.Queries` pasan al objetivo `Landing.Work`. Una consulta de lectura sigue perteneciendo a Work aunque no coordine otras llamadas. **No mover Features a Spaces por su sencillez.**
- Los modelos de lectura con semántica del producto y los Points que consumen sus vistas corresponden a `Landing.Spaces`; las consultas SQL y clientes externos que realizan Capabilities solicitadas por Work, a `Landing.Grounding`. Esto no acredita que las fuentes históricas hayan sido migradas ni que los mecanismos concretos ya estén aprobados.
- Valorar `Shared.Spaces` **solo cuando las definiciones representan verdaderamente la misma semántica y admisibilidad entre consumidores**, tras examinar ownership y diferencias de contexto; no crear un repositorio compartido por parecido nominal o por evitar duplicación superficial. No transferir invariantes autoritativas de Accounts/Identity hacia Landing.
- Los tipos pueden centralizar representación semánticamente coherente para evitar formatos manuales repetidos en las vistas; distinguirla de preferencias locales, cultura, unidad y otras reglas contextuales.
- `Landing.Views` presenta; `Landing.Hosting` configura DI y runtime del producto. Ninguno redefine la responsabilidad conceptual de Spaces, Work o Grounding. Los proyectos de Product se despliegan juntos **por defecto**; separaciones como un cliente nativo se justifican caso a caso. No confundir Hosting con Composition E2E.
- Al probar: verificar admisibilidad y representación en Spaces; Features de consulta y coordinación en Work con Capabilities controladas; contratos HTTP/SQL en Grounding; experiencia en Views; cableado en Hosting; compatibilidad transversal en Composition. Registrar qué se ejecutó.

## Proyecciones y contratos de fuentes en Products

- Reconocer la diferencia entre **semántica canónica de lectura** definida en Product.Spaces, **Feature lectora** de Product.Work y **realización/proyección** en Product.Grounding. La fuente de datos externa no define automáticamente lo que la vista necesita.
- No convertir una fuente canónica en obligación de crear esquema SQL, vista, tabla materializada o usar un ORM específico; el mecanismo se decide tras observar presión, contratos y garantías. Una misma Feature puede combinar varias fuentes sin absorber la autoridad de escritura de los Services.
- Probar Spaces y Work con capacidades controladas; probar Grounding contra el motor y contratos adecuados; comprobar la compatibilidad de migraciones de las fuentes reales mediante Composition. Mocks o esquemas inventados no demuestran compatibilidad entre fuentes versionadas.
- En Serviu Landing, una **misma base SQL Server** para Landing, Accounts e Identity es condición de operabilidad de desarrollo/QA/PROD, no regla universal del Framework. Ver [bootstrap de Landing](https://github.com/atom-dev-serviu/landing-product/blob/main/BOOTSTRAP.md). Separarla exige alerta de riesgos, mecanismos compensatorios y nuevas pruebas.

## Procedimiento al modificar capacidades
1. Consultar el código, contratos y referencias vigentes de Framework y del servicio consumidor. Distinguir expresamente la definición conceptual, su expresión en Language Specification y el comportamiento observado en una realización; **la relación exacta Framework–Language Specification sigue pendiente de revisión**.
2. Identificar conceptos y Points involucrados, su admisibilidad y qué autoridad define sus condiciones.
3. Describir intención, entrada, salida y promesa de resultado de la Feature sin comenzar por el transporte o la persistencia.
4. Identificar Capabilities solicitadas, Guarantees necesarias y dónde Grounding puede realizarlas; distinguir lo requerido de lo comprobado.
5. Examinar composición, fallos parciales y compatibilidad; realizar cambios mínimos, pruebas apropiadas y documentar la evidencia. Para casos de implementación, contrastar con un ejemplo real de Framework o del servicio; si no hay ejemplo verificable, no convertir un patrón supuesto en convención.
6. Explicar **beneficio → costo → límite** de las decisiones cuando corresponda; señalar preguntas abiertas sin inventar contratos del Framework.

Consultar [significados y contraejemplos](references/semantics-and-rationale.md) cuando la tarea tenga ambigüedad conceptual y [fuentes y casos de evaluación](references/sources-and-cases.md) al trabajar con mecanismos o lenguaje.

## Organización y nombres de proyectos (convención de consumidor)
El **repositorio** usa el dominio en singular (`identity-service`), mientras que los **proyectos `.csproj` y sus namespaces base** usan el plural (`Identities.Spaces`, `Identities.Work`, `Identities.Grounding`, `Identities.Hosting` y, solo cuando exista una decisión de crear esa superficie auxiliar, `Identities.Toolkit`). El singular del repositorio es un identificador no ambiguo; el plural de los proyectos evita colisiones entre el nombre del espacio/namespace y tipos de dominio homónimos. Mantener esa regla también en proyectos de pruebas (`Identities.Tests.Regression`). En renombrados, actualizar directorios, `.csproj`, `ProjectReference`, namespaces, imports, pruebas, pipelines y documentación; no renombrar conceptos singulares como `Identity` solo por cambiar el namespace base.

En la migración de Identity Service, usar `src/Identities.Spaces`, `src/Identities.Work`, `src/Identities.Grounding`, `src/Identities.Hosting` como proyectos que materializan las superficies correspondientes; no derivar de su ubicación contratos conceptuales nuevos. Mantener las dependencias del servicio bajo `dependencies/` (por ahora `TerritorialDivisions` como código directo, no submódulo de Composition). Mantener pruebas actuales en `tests/Identities.Tests.Regression`; `tests/Identities.Tests.Progression` es una intención experimental, **no crearla aún**. `Hosting` es el nombre adoptado para ensamblar y activar exposiciones; `Toolkit` es candidato auxiliar, **no** un proyecto que deba crearse automáticamente.

## Límites
No asumir que esta Skill se activa por existir en GitHub: comprobar su instalación y la accesibilidad de fuentes, o declarar la limitación. No declarar que la sintaxis VSIR nueva, Flow, WorkFlow, WorkProcess o WorkStep ya tienen contratos cerrados cuando la fuente no lo demuestre. No convertir una forma observada de la implementación .NET en regla conceptual universal. Mantener separado el diseño de capacidades de la organización Service/Product/Composition: consultar `vslices-solution-architecture` cuando la tarea atraviese esos límites.
