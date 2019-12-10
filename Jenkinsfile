pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/stevenkei/coursework_2.git'
            }
        }
          stage('SonarQube analysis') {
            steps {
                def scannerHome = tool 'SonarScanner';
                 withSonarQubeEnv('SonarQube') {
                  bat "${scannerHome}/bin/sonar-scanner.bat"
                 }
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
