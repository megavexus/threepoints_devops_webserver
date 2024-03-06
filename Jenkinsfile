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
        stage('Pruebas de SAST'){
            steps {
                echo '“Ejecución de pruebas de SAST'
            }
            
        }
        //‘docker build -t devops_ws
        stage('Build'){
            //agent {
            //    dockerfile { 
            //        filename 'Dockerfile.build'
            //        dir './'
            //    }
            //}
            steps{
                bat 'docker build -t devops_ws . '
            }
        }
    }
}
