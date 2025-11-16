pipeline {
    agent any

    stages {
        stage('Clonar repositorio') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/alejonicks/practica-configuracion.git'
            }
        }

        stage('Mostrar versión') {
            steps {
                script {
                    def version = readFile('version.txt')
                    echo "Versión actual del proyecto: ${version}"
                }
            }
        }

        stage('Construcción simulada') {
            steps {
                echo 'Ejecutando build...'
            }
        }

        stage('Despliegue con Docker Compose') {
            steps {
                echo 'Simulando despliegue con Docker Compose...'
            }
        }
    }
}
