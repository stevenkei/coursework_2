pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/stevenkei/coursework_2.git'
            }
        }
        stage('Sonarqube Test') {
            environment {
                scannerHome = tool 'SonarScanner'
            }
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
                timeout(time: 1, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
        stage("Docker") {
            steps {
                 docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
                }
            }
        }
    }
}
