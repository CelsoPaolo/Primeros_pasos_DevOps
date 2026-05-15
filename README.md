##  Resumen del Procedimiento Realizado

Para cumplir con los objetivos del seminario, se llevó a cabo un proceso de reconstrucción y ejecución técnica dividido en las siguientes etapas:

### 1. Preparación del Escenario (Infraestructura como Código)
Debido a que los recursos originales del video no estaban disponibles, se procedió a:
* **Instalación y Configuración de Docker Desktop**: Configuración del motor de contenedores con soporte para WSL 2 en Windows para garantizar un entorno de pruebas aislado.
* **Orquestación con Docker Compose**: Creación de un archivo `docker-compose.yml` utilizando una imagen alternativa funcional (`nickvth/phpunit-rce`) para simular el servidor vulnerable.

### 2. Desarrollo de la Herramientas de Automatización
Se desarrolló un script de post-explotación en **Python 3** utilizando la librería `requests`. 
* **Lógica del Script**: El programa automatiza el envío de payloads mediante peticiones HTTP POST dirigidas al componente vulnerable de PHPUnit (`eval-stdin.php`), permitiendo la ejecución de comandos remotos (RCE).

### 3. Resolución de Obstáculos Técnicos (Troubleshooting)
Durante la práctica se identificaron y solucionaron los siguientes puntos críticos:
* **Gestión de Rutas**: Corrección de errores de directorio (`No such file or directory`) mediante navegación en terminal (`cd`).
* **Gestión de Dependencias**: Instalación de módulos faltantes en el entorno local de Python (`pip install requests`).
* **Conectividad de Red**: Configuración de mapeo de puertos (`8080:80`) para permitir la comunicación entre la máquina host y el contenedor.

### 4. Prueba de Concepto y Validación
Se validó el éxito de la práctica ejecutando comandos de sistema dentro del contenedor desde la terminal de VS Code:
* Comando `whoami`: Confirmó la identidad del usuario del servidor web (`www-data`).
* Comando `ls`: Permitió listar archivos del sistema raíz, confirmando el compromiso total del contenedor.
