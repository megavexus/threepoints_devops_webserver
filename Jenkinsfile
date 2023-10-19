pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'andresospina0000', url: 'https://github.com/andresospina0000/threepoints_devops_webserver'
            }
        }
        stage('Pruebas de SAST') {
            steps {
                @echo “Ejecución de pruebas de SAST”
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