pipeline {
    agent any 
    stages {
        stage('Clean') { 
            steps {
                git clone "https://github.com/stevenkei/coursework_2.git"
            }
        }
        stage('SonarQube Test') {
    def scannerHome = tool 'SonarScanner 4.0';
    withSonarQubeEnv('My SonarQube Server') {
      sh "${scannerHome}/bin/sonar-scanner"
            }
        }
        stage('Deploy') { 
            steps {
                sh "mvn package" 
            }
        }
    }
}
