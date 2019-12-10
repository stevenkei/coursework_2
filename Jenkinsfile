pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/stevenkei/coursework_2.git'
            }
        }
        stage('Build && SonarQube Test') {
            steps {
                scannerHome = tool 'SonarQube'
                withSonarQubeEnv('SonarQube') {
                    sh "${scannerHome}/bin/sonar-runner"
                }
            }
        }
        stage("Quality Gate") {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
