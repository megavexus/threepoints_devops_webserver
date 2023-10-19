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
                withSonarQubeEnv(installationName: 'Sonar Local',credentialsId: 'AO_Token') {
                    sh "${tool("SonarScanner")}/bin/sonar-scanner -Dsonar.projectKey=threepoints_devops_webserver -Dsonar.projectName=threepoints_devops_webserver"
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