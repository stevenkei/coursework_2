pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                checkout scm
            }
        }
        stage('Sonarqube Test') {
            environment {
                scannerHome = tool 'SonarQube'
            }
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
        stage("Docker Image") {
            steps {
                script {
                    def app = docker.build("stevenkei/coursework_2:tag")
                 docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                    app.push("latest")
                    }
                }
            }
        }
    }
}
