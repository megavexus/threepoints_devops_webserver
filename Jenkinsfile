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
                echo 'Ejecución de pruebas de SAST'
            }
        }
        stage('Configurar archivo') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'Credentials_Threepoints', passwordVariable: 'password', usernameVariable: 'username')]) {
                    writeFile(file: 'ArchivoConf.txt', text: "[credentials] \nusername=${username} \npassword=${password}")
                    sh "ls -l"
                    sh 'cat ArchivoConf.txt'
                    archiveArtifacts artifacts: 'ArchivoConf.txt'
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