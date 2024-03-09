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
                  withSonarQubeEnv('SonarQubeTarea1') {
                      sh """
                        sonar-scanner \
                        -Dsonar.projectKey=sonarqube \
                        -Dsonar.sources=. \
                        -Dsonar.login=sqa_a413ae3509c14988687d7bb1a9ca36370997bc5f
                      """
                    }
                  timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: false
                    }
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
