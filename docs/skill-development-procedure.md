# Procedimiento para construir y revisar Skills con cobertura semántica

**Estado:** propuesta operativa inicial, 29-10-2026. Debe revisarse mediante usos reales. Aplicable inicialmente a `vslices-solution-architecture` y `vslices-capability-architecture`.

## Qué significa «lo más completa posible»

Completa **para sus responsabilidades**, no exhaustiva en cantidad de texto. La Skill ha de:
- activarse en tareas que realmente necesitan su criterio y no en otras;
- representar correctamente conceptos, límites, razones y trade-offs;
- orientar acciones de desarrollo observables;
- distinguir fuentes, decisiones, hipótesis y evidencia;
- localizar información vigente en vez de congelar detalles mutables;
- detectar conflictos y reconocer lo desconocido;
- conservar sus garantías cuando cambian implementaciones.

No confundir «explicación convincente» con propaganda: explicar beneficios esperados **y costos**, límites y situaciones donde la decisión debe reexaminarse.

## Ciclo propuesto (evidencia → Skill → evaluación → revisión)

### 1. Identificar la responsabilidad y el disparador

Declarar en una frase:
- qué clase de problemas resuelve;
- quién necesita la capacidad y cuándo;
- qué decisiones debe facilitar;
- qué asuntos quedan fuera;
- cómo reconocer que la Skill **no** corresponde a la tarea.

**Ejemplo:** `vslices-solution-architecture` se activa cuando un agente crea o modifica código, contratos, pruebas o despliegues que atraviesan Service/Product/Composition de VSlices. No debe activarse por una consulta general de arquitectura sin relación con VSlices/Serviu.

### 2. Recuperar autoridad y procedencia

Consultar fuentes canónicas y código real. Registrar por distinción:
- definición y dueño de la semántica;
- decisión aprobada o preferencia;
- realización observada;
- pruebas existentes y garantías no comprobadas;
- tensión o pregunta abierta.

No deducir reglas de nombres de carpetas, tests que no se han ejecutado o código legado aislado. Distinguir el diseño objetivo de realizaciones anteriores.

### 3. Construir ejemplos contrastables, también negativos

Definir una pequeña colección de tareas realistas antes de escribir grandes instrucciones:
- **positivas directas:** el agente aplica la decisión correctamente;
- **de frontera:** dos autoridades interactúan y el ownership puede confundirse;
- **negativas:** no debe mover una responsabilidad ni activar la Skill cuando no corresponde;
- **con información incompleta:** debe investigar o declarar incertidumbre;
- **con contradicción:** debe comunicar el conflicto sin inventar acuerdo;
- **regresivas:** un cambio local debe verificarse en consumidores.

Ejemplos iniciales para Solution Architecture:
1. Agregar una regla de credenciales solicitada desde Landing: autoridad de Accounts, experiencia de Landing.
2. Crear la página de aplicaciones accesibles: proyección de Landing; autorizaciones y catálogo no inventados por la UI.
3. Cambiar Account Service y aprobar CI local: **no basta** para publicar; matrices de composiciones consumidoras afectadas.
4. Añadir un servicio a Landing Composition: submódulo con gitlink fijado, configuración SQL Server, pruebas de integración; Composition no adquiere su lógica.
5. Pedir mover `ProfileQuery` a Identity por leer identidades: explicar por qué la proyección especializada puede ser del producto.
6. Proyecto no relacionado con VSlices: no imponer esta arquitectura.

Para Capability Architecture, **recolectar primero ejemplos del Framework real**. No diseñar ejemplos normativos a partir de equivalencias con Clean Architecture.

### 4. Escribir el contenido mínimo que permita decidir

Distribuir:
- `SKILL.md`: disparadores, flujo operativo conciso, criterios de decisión y cuándo consultar referencias;
- `references/semantics.md`: definiciones, separaciones y ejemplos;
- `references/rationale.md`: beneficios esperados, costos, fallas y contraejemplos;
- `references/sources.md`: localización de autoridades y referencias actuales;
- `agents/openai.yaml`: metadatos de presentación.

Evitar duplicar contratos de los repositorios de servicios/productos/composiciones. Explicar cómo consultarlos al trabajar. Incorporar scripts **solo** cuando la operación sea repetitiva/determinista y se beneficie de ejecución, no para sustituir juicio semántico.

### 5. Evaluar activación y comportamiento

Ejecutar los mismos casos **con Skill y sin Skill** en una sesión/agente de prueba, procurando no entregar las respuestas esperadas como parte de la solicitud. Revisar:
- **activación:** se usa cuando corresponde; no interrumpe tareas ajenas;
- **exactitud:** la clasificación Service/Product/Composition o Spaces/Work/Grounding concuerda con las fuentes;
- **aplicación:** los cambios de código/contratos respetan las fronteras;
- **explicación:** el agente justifica la decisión con beneficios y costos pertinentes;
- **procedencia:** referencia evidencia correcta y marca hipótesis;
- **regresión:** exige y ejecuta las verificaciones requeridas cuando dispone de herramientas;
- **autonomía responsable:** puede actuar dentro del alcance autorizado y no se adjudica decisiones o pruebas no realizadas.

Conservar casos que fallen como **regresiones de la Skill**. Evitar optimizar solo para las frases exactas de los casos; variar lenguaje, repositorio y escenario.

### 6. Validar empaquetado y distribución

Usar el formato de Agent Skills (carpeta con `SKILL.md` y frontmatter `name` / `description`); validar estructura, referencias y metadatos con herramientas de `skill-creator`. Si la Skill se instalará como ZIP, empaquetarla y comprobar que otro agente puede descubrirla. Un validador de estructura **no demuestra calidad semántica**.

Comprobar que las fuentes externas son accesibles desde el entorno consumidor. Una Skill instalada sin acceso a sus contratos canónicos debe declarar esa limitación, no suplir la lectura con conjeturas.

### 7. Revisar por evidencia, no por acumulación

Cuando un caso real revele una brecha:
```text
caso → conducta observada → distinción faltante → cambio mínimo de Skill
     → repetición de evaluación → decisión de mantener/promover
```
Registrar cambios que alteren significado o criterio. Reexaminar disparadores y ejemplos negativos; retirar instrucciones redundantes o superadas. Evitar crecer por completitud ornamental.

## Criterios de cierre de una primera versión

Una Skill puede considerarse lista para uso inicial cuando:
1. Tiene límites/disparadores claros y una fuente de autoridad reconocible.
2. Supera una batería explícita de casos positivos, fronterizos y negativos.
3. Explica por qué se trabaja de cierta forma, incluidos costos y alternativas.
4. Produce comportamiento correcto en una modificación o análisis real.
5. No inventa pruebas, permisos, decisiones ni mecanismos implementados.
6. Su estructura ha sido validada y probada desde una instalación limpia.
7. Las limitaciones restantes quedan documentadas.

**No existe garantía de completitud universal**; los casos reales seguirán descubriendo límites. La meta es una Skill pequeña, revisable y capaz de conservar criterio.

## Aplicación inicial a VSlices

Primero construir/evaluar `vslices-solution-architecture` con los cuatro contratos recientes de Serviu. Para `vslices-capability-architecture`, recuperar primero las definiciones canónicas y examinar implementaciones concretas de Spaces, Work y Grounding. Las Skills deberán ser complementarias pero invocables por separado. No asignar a ellas autoridad para rediseñar la arquitectura.
