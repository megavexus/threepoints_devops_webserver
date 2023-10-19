pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'andresospina0000', url: 'https://github.com/andresospina0000/threepoints_devops_webserver'
            }
        }
        stage('Pruebas de SAST') {
            parallel{
                stage('Pruebas de SAST - Hilo 1'){
                    steps {
                        echo 'Hilo 1 - Ejecución de pruebas de SAST'
                    }
                }
                stage('Impresion WORKSPACE - Hilo 2'){
                    steps {
                        echo "Hilo 2 - Path del WORKSPACE: ${WORKSPACE}"
                    }
                }
            }
        }
        stage('Build') {
            steps {
                // Usamos docker build para construir el container (o artefacto) resultante
                sh 'docker build -t devops_ws .'
            }
        }
        
    }
}