pipeline {
    agent any

    stages {
        stage('Clonar Repositorio') {
            steps {
                git branch: 'main', credentialsId: 'tus-credenciales-github', url: 'https://github.com/RoNy2294/ProyectoFullstack.git'
            }
        }

        stage('Construir Frontend') {
            steps {
                    bat 'npm install'
                    bat 'npm run build'          
            }
        }

        // Etapas para pruebas y despliegue ...

        stage('Pruebas de Modulos') {
            steps {
                script {
                    def modules = ['categoria.py', 'foro.py', 'noticia.py', 'orden.py', 'producto.py', 'rol.py', 'usuario.py']

                    for (module in modules) {
                        echo "Ejecutando pruebas en el módulo: $module"
                        bat "python $module"
                    }
                }
            }
        }
		stage('Pruebas de Controllers') {
            steps {
                script {
                    def modules = ['asignar-rol.py', 'buscar-foro.py', 'comprar-producto.py', 'consultas.py', 'filtrar-producto.py',
				    'foro.py', 'noticias.py', 'productos.py', 'recuperar_contraseña.py', 'registrar.py', 'respuesta-foro.py']

                    for (module in modules) {
                        echo "Ejecutando pruebas en el módulo: $module"
                        bat "python $module"
                    }
                }
            }
        }
		stage('Ejecutar Pruebas SQL') {
            steps {
                script {
                    bat 'psql -U tu-usuario -d tu-base-de-datos -a -f tests.sql'
                }
            }
        }
        stage('Desplegar') {
            steps {
                bat './deploy.bat'
            }
        }
    }
}
