# Comprobación Técnica – Práctica 11

## ¿Qué hace el bloque upstream?
El bloque `upstream` define un grupo de servidores backend (web1, web2, web3) a los que NGINX enviará las peticiones usando un algoritmo round-robin.

## ¿Cómo se configuran los healthchecks?
En `docker-compose.yml` se usa la directiva `healthcheck`, que consulta el endpoint `/status` para comprobar si la instancia está funcionando correctamente.

## ¿Cómo se pasa tráfico de NGINX a Flask?
NGINX actúa como proxy inverso y redirige las peticiones al backend usando `proxy_pass` hacia el grupo definido en `upstream`.

## ¿Qué puertos se usan?
- Puerto **8080**: acceso del cliente a NGINX.
- Puerto **80**: NGINX dentro del contenedor.
- Puerto **8000**: Gunicorn y Flask.

## ¿Qué función tiene Gunicorn?
Gunicorn es un servidor WSGI que ejecuta la aplicación Flask de forma eficiente y preparada para producción, permitiendo múltiples procesos y mejor rendimiento que el servidor de desarrollo.
