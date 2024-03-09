pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Descarga de código
                git branch: 'master', credentialsId: 'gitJenkins', url: 'https://github.com/mdeclementi/threepoints_devops_webserver.git'
            }
        }

        stage('Pruebas de SAST') {
        steps {
        script {
            def scannerHome = tool 'sonar-scanner'
            withEnv(["PATH+SONAR=${scannerHome}/bin"]) {
                sh """
                    sonar-scanner \
                    -Dsonar.projectKey=sonarqube \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=http://localhost:9000 \
                    -Dsonar.token=squ_217b85f8c5815385dfa19b71a1aa03bb0079e16d
                """
            }
        }
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
