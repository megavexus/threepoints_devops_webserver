pipeline {
    agent any

    // parameters {
    //     credentials(name: 'Credentials_access', description: 'Credenciales de usuario y contraseña', defaultValue: 'alexcst90', credentialType: 'Username with password', required: true)
    // }
    stages {
            stage('Checkout') {
                steps {
                    // Get some code from a GitHub repository
                    git 'https://github.com/alexcst90/threepoints_devops_webserver.git'

                    // Run Maven on a Unix agent.
                    //sh "mvn -Dmaven.test.failure.ignore=true clean package"

                }

            
            }
            // stage('Configurar archivo'){
            //     steps{
            //         script {
            //             withCredentials([usernamePassword(credentialsId: 'Credentials_Threepoints', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
            //                 //bat "echo '[credentials]' > credentials2.ini"
            //                 //bat "echo 'user=${USERNAME}' >> credentials2.ini"
            //                 //bat "echo 'password=${PASSWORD}' >> credentials2.ini"
            //             }
            //         }
            //         post {
            //             always {
            //                 archiveArtifacts artifacts: 'credentials.ini'
            //             }
            //         }
            //     }
            // }
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

