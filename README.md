📘 Práctica: Pipeline CI/CD con Jenkins, Git y Docker Compose

Esta práctica consiste en implementar un flujo completo de integración y despliegue continuo (CI/CD) utilizando GitHub, Jenkins y Docker Compose.
El objetivo principal es que, cada vez que se realice un git push al repositorio, se ejecute un pipeline que actualice y despliegue automáticamente un contenedor Nginx.

🚀 Tecnologías Utilizadas

Git / GitHub → Control de versiones

Jenkins → Automatización con Pipeline declarativo

Docker → Contenedores

Docker Compose → Orquestación de servicios

🗂️ Estructura del Proyecto
practica-configuracion/
│
├── deploy/
│   └── docker-compose.yml
│
└── Jenkinsfile

🔄 Flujo de CI/CD Implementado
✅ 1. Control de versiones con Git

El repositorio utilizado en la práctica es:

👉 https://github.com/alejonicks/practica-configuracion.git

Cada vez que se realiza un push a la rama main, Jenkins ejecuta automáticamente el pipeline.

✅ 2. Pipeline en Jenkins

Se configuró un pipeline llamado pipeline-practica, conectado directamente al repositorio.

El pipeline realiza:

Checkout del repositorio

Detiene el despliegue anterior (docker compose down)

Levanta el nuevo despliegue (docker compose up -d)

Refresca el entorno automáticamente con cada cambio

Fragmento del pipeline (Jenkinsfile):

stage('Deploy') {
    steps {
        sh 'cd deploy && docker compose down || true'
        sh 'cd deploy && docker compose up -d --build'
    }
}

✅ 3. Despliegue con Docker Compose

El archivo docker-compose.yml utiliza la imagen oficial nginx:latest, exponiendo el servicio en:

👉 http://localhost:8081

Esto permite visualizar el resultado del despliegue desde el navegador.

🧪 Resultados de la Práctica

✔ Jenkins detecta automáticamente los cambios del repositorio

✔ El pipeline ejecuta correctamente (Build #10 en estado SUCCESS)

✔ El contenedor practica_nginx se levanta sin errores

✔ Acceso al servicio desde el navegador:
👉 http://localhost:8081

📷 Evidencias del funcionamiento

Pipeline ejecutado en Jenkins

Log del pipeline mostrando ejecución exitosa

Contenedor activo en Docker (docker ps)

Servicio Nginx funcionando
