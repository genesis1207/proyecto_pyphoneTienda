pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Validar archivos') {
            steps {
                sh '''
                    echo "Validando estructura del proyecto..."
                    test -f index.html
                    test -f checkout.html
                    test -f response.html
                    echo "OK: archivos principales presentes"
                '''
            }
        }

        stage('Desplegar') {
            steps {
                sh '''
                    echo "Copiando archivos al servidor de producción (Nginx)..."
                    rm -rf /deploy/*
                    cp -r ./* /deploy/
                    echo "Despliegue completado en /deploy"
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline ejecutado con éxito. PayphonePractica desplegada en producción.'
        }
        failure {
            echo '❌ El pipeline falló. Revisa los logs arriba.'
        }
    }
}