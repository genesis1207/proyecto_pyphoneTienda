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
                sh '''
                    echo "========== INICIO DE PRUEBAS =========="

                    echo "Test 1: Verificar que existe index.html"
                    test -f index.html
                    echo "✔ Test 1 aprobado"

                    echo "Test 2: Verificar que existe checkout.html"
                    test -f checkout.html
                    echo "✔ Test 2 aprobado"

                    echo "Test 3: Verificar que existe response.html"
                    test -f response.html
                    echo "✔ Test 3 aprobado"

                    echo "Test 4: Verificar que existe README.md"
                    test -f README.md
                    echo "✔ Test 4 aprobado"

                    echo "Test 5: Verificar que existe Jenkinsfile"
                    test -f Jenkinsfile
                    echo "✔ Test 5 aprobado"

                    echo "========== TODOS LOS TESTS FUERON APROBADOS =========="
                '''
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