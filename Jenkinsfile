node {
  stage('SCM') {
    git 'https://github.com/stevenkei/coursework_2.git'
  }
  stage('SonarQube analysis') {
    def scannerHome = tool 'SonarScanner 3.3.0.1492';
    withSonarQubeEnv('My SonarQube Server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
