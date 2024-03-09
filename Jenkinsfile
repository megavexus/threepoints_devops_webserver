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
                  withSonarQubeEnv('sonar-scanner') {
                      sh """
                        sonar-scanner \
                        -Dsonar.projectKey=sonarqube \
                        -Dsonar.sources=. \
                        -Dsonar.login=squ_217b85f8c5815385dfa19b71a1aa03bb0079e16d
                      """
                    }
                  timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: false
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
