pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Descarga de código
                git 'https://github.com/mdeclementi/threepoints_devops_webserver.git'
            }
        }

        stage('Pruebas de SAST') {
            steps {
                // Ejecución de pruebas de calidad de código
                echo 'Ejecución de pruebas de SAST'
            }
        }

        stage('Build') {
            steps {
                // Construcción del container de Docker
                script {
                    sh 'docker build -t devops_ws .'
                }
            }
        }
    }
}
