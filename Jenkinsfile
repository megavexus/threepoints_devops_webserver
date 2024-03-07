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
          
      stage('Imprimir Env'){

                parallel{
                    
                    stage('Pruebas de SAS'){
                        steps {
                            echo "Variable de entorno Workspace: ${WORKSPACE}"
                        }
                    }



                    stage('Build'){
                        steps{
                            bat 'docker build -t devops_ws . '
                        }
                    }

                }
                
            }
                
                
            
        }
    }

