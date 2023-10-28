pipeline {
    agent any

    stages {
        stage('Clonar Repositorio') {
            steps {
                // Clonar el repositorio desde GitHub
                git branch: 'main', credentialsId: 'tus-credenciales-github', url: 'https://github.com/tu-usuario/tu-repositorio.git'
            }
        }

        stage('Construir Frontend') {
            steps {
                dir('view') {
                    // Aquí puedes ejecutar comandos para construir el frontend
                    // Por ejemplo, si utilizas npm:
                    bat 'npm install'
                    bat 'npm run build'
                }
            }
        }

        // ... Otras etapas para pruebas y despliegue ...

        stage('Desplegar') {
            steps {
                // Realiza el despliegue de tu proyecto
                // Esto puede variar según tu infraestructura y preferencias
                // Puedes utilizar scripts personalizados aquí
                bat './deploy.bat'
            }
        }
    }
}
