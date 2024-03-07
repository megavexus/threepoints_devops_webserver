pipeline {
    agent any

  
    stages {
            stage('Checkout') {
                steps {
                    // Get some code from a GitHub repository
                    git 'https://github.com/alexcst90/threepoints_devops_webserver.git'

                    // Run Maven on a Unix agent.
                    //sh "mvn -Dmaven.test.failure.ignore=true clean package"

                }

            
            }
          
     
            stage('Pruebas de SAS'){
                steps {
                    echo 'sonarqube env'
                    withSonarQubeEnv('My SonarQube Server', envOnly: true) {
                        // This expands the evironment variables SONAR_CONFIG_NAME, SONAR_HOST_URL, SONAR_AUTH_TOKEN that can be used by any script.
                        println ${env.SONAR_HOST_URL} 
                    }
                }
            }



            stage('Build'){
                steps{
                    bat 'docker build -t devops_ws . '
                }
            }

                
                
            
        }
    }

