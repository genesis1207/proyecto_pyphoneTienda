pipeline {
    agent any

    stages {

        stage('Clonar repositorio') {
            steps {
                checkout scm
                echo 'Repositorio clonado correctamente.'
            }
        }

        stage('Build') {
            steps {
                echo 'Construyendo proyecto...'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    echo "Iniciando despliegue..."
                    cp -rf ./* /deploy/
                    echo "Despliegue completado."
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline ejecutado correctamente.'
        }

        failure {
            echo 'Hubo un error en el Pipeline.'
        }

        always {
            echo 'Fin del Pipeline.'
        }
    }
}