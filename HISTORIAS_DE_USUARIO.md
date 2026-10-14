# Historias de usuario - Infraestructura

## HU-01: Levantar entorno local

Como desarrollador, quiero ejecutar la infraestructura local con Docker para poner en marcha la biblioteca sin configuración manual compleja.

Criterios de aceptación:

- El proyecto levanta contenedores de la aplicación y la base de datos.
- La red y los volúmenes quedan definidos y reutilizables.
- Las variables de entorno quedan encapsuladas en un archivo de ejemplo.

## HU-02: Aislar dependencia de servicios

Como equipo, quiero separar los servicios de la app y la base de datos para facilitar mantenimiento y despliegue.

Criterios de aceptación:

- La composición de servicios define cada componente con su propósito específico.
- La infraestructura permite reinicios y pruebas sin conflictividad.
- Los datos persistentes quedan en volúmenes controlados.

## HU-03: Preparar base de datos

Como desarrollador, quiero contar con un motor de base de datos preparado para la aplicación para soportar CRUD y consultas.

Criterios de aceptación:

- La base de datos queda definida en la composición.
- Existe una configuración mínima del entorno y credenciales de ejemplo.
- La capa de datos está lista para migraciones del backend.

## HU-04: Soportar despliegue de la solución

Como equipo de entrega, quiero que la infraestructura pueda servir como base del despliegue para mantener un entorno reproducible.

Criterios de aceptación:

- El repositorio incluye una referencia clara de cómo levantar el stack.
- La configuración es portable entre equipos de desarrollo.
- Los archivos de entorno siguen patrones seguros y documentados.
