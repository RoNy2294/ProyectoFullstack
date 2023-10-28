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
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }

        stage('Construir Backend') {
            steps {
                dir('backend') {
                    // Aquí puedes ejecutar comandos para construir el backend
                    // Asumiendo que utilizas Maven para Java:
                    sh 'mvn clean package'
                }
            }
        }

        stage('Pruebas Frontend') {
            steps {
                dir('view') {
                    // Ejecuta pruebas para el frontend si las tienes
                    // Por ejemplo, utilizando un marco de prueba como Jest
                    sh 'npm run test'
                }
            }
        }

        stage('Pruebas Backend') {
            steps {
                dir('backend') {
                    // Ejecuta pruebas para el backend si las tienes
                    // Asumiendo que utilizas JUnit para Java
                    sh 'mvn test'
                }
            }
        }

        stage('Desplegar') {
            steps {
                // Realiza el despliegue de tu proyecto
                // Esto puede variar según tu infraestructura y preferencias
                // Puedes utilizar scripts personalizados aquí
                sh './deploy.sh'
            }
        }
    }
}

                sh 'python deploy.py'
            }
        }
    }
}
