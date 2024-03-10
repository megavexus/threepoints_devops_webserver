@Library("my-libary") _
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
                            
                            sonarAnalysis()
                            
                           

                        }
                       
                    }



                    stage('Build'){
                        steps{
                            echo 'building...'
                            // bat 'docker build -t devops_ws . '
                        }
                    }
                }
                    
                
            }
        
            // stage('Despliegue del servidor'){
            //     steps{
            //        bat 'docker stop devops_ws || true'
            //     //    bat 'docker run -d -p 8090:8090 --name devops devops_ws'
            //     }
            //     // steps{
            //     //     bat 'docker run -d -p 8090:8090 --name devops devops_ws'
            //     // }
            // } 
                
            
        
    }
    // post{
    //     always{
    //        // bat 'docker stop devops_ws || true'
    //         bat 'docker run -d -p 8090:8090 --name devops devops_ws'
    //     }
    // }
}

