# Semántica y razones

## Spaces
Las definiciones de Space permiten hablar de Points admisibles y de las condiciones que respetan. **Beneficio:** las Features consumen conceptos sin poder redefinir arbitrariamente su significado. **Costo:** exige explicitar reglas y detectar incompatibilidades. No confundir Space con agregado DDD, tabla ni namespace.

## Work
La responsabilidad de Work es expresar comportamiento, capacidades y composición. Una Feature tiene intención, entrada, salida y promesa de resultado, incluso cuando tipos como Unit sean convencionales. **Beneficio:** el comportamiento conserva intención comprensible sin estar subordinado a un efecto o runtime. **Costo:** declarar obligaciones no garantiza su realización; las composiciones introducen condiciones adicionales. No inferir que secuencia significa transacción.

## Grounding
Proporciona una realización para capacidades necesarias, sujeta a condiciones del entorno y garantías. **Beneficio:** permite distinguir comportamiento requerido del mecanismo elegido y examinar si las garantías se cumplen. **Costo:** selección, configuración y observación de realizaciones. **Contraejemplo:** asumir que EF Core o SQL Server por sí solos prueban aislamiento y durabilidad del proceso completo.

## Fronteras
Estas tres superficies pertenecen a **Framework**, no son reinterpretaciones de capas DDD ni propiedad de Language Specification por el hecho de que allí existan articulaciones para el lenguaje. La existencia de tres superficies reconocidas no establece una taxonomía futura cerrada ni una separación física obligatoria.

## Caso Landing: unificar funcionalidades sin borrar diferencias

Una pantalla requiere un perfil: **Work** define la Feature de consulta y su resultado; **Spaces** da significado a los datos y a las representaciones coherentes; **Grounding** realiza la lectura, con garantías contrastadas respecto de la autoridad del esquema. Que la Feature sea una sola lectura no la desplaza a Spaces. El antiguo BFF y Queries son procedencia de implementación, no dos autoridades futuras. `Shared.Spaces` solo procede tras verificar identidad semántica y admisibilidad entre dominios.
