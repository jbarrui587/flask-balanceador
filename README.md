# Práctica 11 – Balanceo de Carga Escalable con Flask, Gunicorn, NGINX y Docker

## 1. Descripción del sistema
Este proyecto implementa una arquitectura web escalable y balanceada usando contenedores Docker.  
El sistema está compuesto por:

- **Flask**: aplicación web sencilla.
- **Gunicorn**: servidor WSGI para ejecutar Flask en producción.
- **NGINX**: balanceador de carga y proxy inverso.
- **Docker Compose**: orquestación de múltiples servicios.
- **GitHub**: control de versiones y documentación.

NGINX recibe todas las peticiones del cliente y las distribuye entre **tres instancias** de Flask usando el algoritmo **round-robin**.
Arquitectura:

[ Cliente / Navegador ]
|
[ NGINX ] (puerto 8080)
/ |
[ web1 ][ web2 ][ web3 ]
(Flask + Gunicorn)

## 2. Despliegue del sistema

### Requisitos
- Docker
- Docker Compose
- Git

### Pasos
1. Clonar el repositorio:
   ```bash
   git clone https://github.com/jbarrui587/flask-balanceador.git
   cd flask-balanceador
Construir y levantar los servicios:

docker compose up --build
Acceder desde el navegador:

http://localhost:8080
3. Estructura del proyecto
.
├── app/
│   ├── application.py
│   └── wsgi.py
├── docker/
│   └── nginx_balanceador.conf
├── scripts/
│   └── test_balanceo.sh
├── capturas/
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── README.md
├── reflexion.md
├── comprobacion.md
└── entrega.json
4. Función de cada archivo
application.py: define las rutas Flask.

wsgi.py: punto de entrada para Gunicorn.

requirements.txt: dependencias del proyecto.

Dockerfile: crea la imagen de la app Flask.

nginx_balanceador.conf: configuración del balanceador NGINX.

docker-compose.yml: coordina todos los servicios.

test_balanceo.sh: script para comprobar el balanceo.

capturas/: evidencias gráficas del funcionamiento.

5. Cómo probar el balanceo
Ejecutar el script:

bash scripts/test_balanceo.sh
O acceder varias veces a:

http://localhost:8080
Se observará que el nombre de la instancia cambia en cada petición.

6. Pruebas de tolerancia a fallos
Detener una instancia:

docker stop web2
El sistema seguirá respondiendo gracias al balanceo de NGINX.

