# Razones, costos y distinciones

## Service
**Beneficio esperado:** reglas y garantías conservan un propietario reconocible y pueden ser consumidas por varias experiencias sin duplicarse. **Costo:** contratos explícitos, coordinación y mayor responsabilidad sobre compatibilidad. **Contraejemplo:** mover reglas de credenciales a Landing por ser la pantalla que las invoca.

## Product
**Beneficio esperado:** experiencias y procesos pueden evolucionar sin apropiarse de la semántica de servicios. Views, BFF y Queries poseen responsabilidades distintas en Serviu, aunque no exigen tres deployments. **Costo:** integración de información, fallos parciales y reglas de presentación requieren examen. **Contraejemplo:** suponer que una Query de perfil pertenece a Identity Service solo porque lee identidades.

## Composition
**Beneficio esperado:** supervisión global de regresiones que no aparecen en tests locales; reproducción de versiones exactas y evidencia para publicar con seguridad. **Costo:** matrices E2E, ambientes, versiones y mantenimiento de compuertas; un número creciente de composiciones incrementa las verificaciones requeridas, no las elimina. **Contraejemplo:** publicar Account Service con tests locales verdes aunque Landing haya dejado de poder iniciar sesión.

## Separaciones negativas
No equiparar límites funcionales a repositorios, procesos, despliegues o servidores. No inferir HTTP como semántica universal. No confundir el Nexus documental de Docs Standard con Composition operacional.

Preguntar ante ambigüedad: ¿quién define las reglas?, ¿quién organiza la experiencia?, ¿quién comprueba la compatibilidad del conjunto?, ¿qué beneficio concreto se pierde al mover esa responsabilidad?
