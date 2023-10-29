pipeline {
    agent any

    // Etapas para pruebas y despliegue ...

        stage('Pruebas de Módulos') {
            steps {
                dir('backend/model') {
                    script {
                        def modules = ['categoria.py', 'foro.py', 'noticia.py', 'orden.py', 'producto.py', 'rol.py', 'usuario.py']

                        for (module in modules) {
                            echo "Ejecutando pruebas en el módulo: $module"
                            sh "python $module"
                        }
                    }
                }
            }
        }
	stage('Pruebas de Controllers') {
            steps {
                dir('backend/controller') {
                    script {
                        def modules = ['asignar-rol.py', 'buscar-foro.py', 'comprar-producto.py', 'consultas.py', 'filtrar-producto.py',
						'foro.py', 'noticias.py', 'productos.py', 'recuperar_contraseña.py', 'registrar.py', 'respuesta-foro.py']

                        for (module in modules) {
                            echo "Ejecutando pruebas en el módulo: $module"
                            sh "python $module"
                        }
                    }
                }
            }
        }
	stage('Ejecutar Pruebas SQL') {
            steps {
                dir('https://github.com/RoNy2294/ProyectoFullstack.git') {
                    script {
                        sh 'psql -U rony -d El-Ansuelo -a -f tests.sql'
                    }
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

