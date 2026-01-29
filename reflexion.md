# Reflexión – Práctica 11

## ¿Qué has aprendido sobre balanceo?
He aprendido que el balanceo de carga permite repartir peticiones entre varias instancias para mejorar la disponibilidad, el rendimiento y la tolerancia a fallos del sistema. Si una instancia falla, el servicio puede seguir funcionando.

## ¿Cómo has identificado qué instancia respondía?
Cada respuesta incluye el `hostname` del contenedor usando `socket.gethostname()`. Esto permite ver claramente qué instancia ha procesado cada petición.

## ¿Qué pasaría si NGINX falla?
NGINX es un punto único de fallo. Si se detiene, el sistema dejaría de responder. En producción se usarían varios NGINX o balanceadores externos para evitar este problema.

## ¿Qué mejorarías en este sistema?
- Añadir HTTPS.
- Usar más instancias automáticamente (auto-scaling).
- Implementar un balanceador redundante.
- Añadir monitorización y logs centralizados.

## ¿Qué ventajas ves al usar GitHub?
GitHub permite llevar control de versiones, documentar el proyecto, trabajar en equipo y mantener un historial claro de cambios mediante commits.