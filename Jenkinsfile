pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/stevenkei/coursework_2.git'
            }
        }
        stage('Build && SonarQube Test') {
            environment {
                scannerHome = tool 'SonarScanner'
            }
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
                timeout(time: 1, unit: 'HOURS') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
        stage("Docker") {
            steps {
            }
        }
    }
}
