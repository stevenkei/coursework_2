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
             def scannerHome = tool 'sonarScanner';
             withSonarQubeEnv('SonarQube 6.2') {
             bat "${scannerHome}/bin/sonar-scanner.bat"
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
