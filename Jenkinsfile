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
                echo 'Desplegando aplicación...'

                sh '''
                    cp -r * /deploy/
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline ejecutado correctamente.'
        }

        failure {
            echo 'Hubo un error durante la ejecución.'
        }

        always {
            echo 'Fin del Pipeline.'
        }
    }
}