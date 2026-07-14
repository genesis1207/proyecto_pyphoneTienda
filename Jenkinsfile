pipeline {
    agent any

    stages {

        stage('Clonar repositorio') {
            steps {
                echo 'Clonando repositorio...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Construyendo el proyecto...'
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

                bat '''
                if not exist C:\\deploy mkdir C:\\deploy
                xcopy /E /Y * C:\\deploy\\
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline ejecutado correctamente'
        }

        failure {
            echo 'Hubo un error en el pipeline'
        }
    }
}