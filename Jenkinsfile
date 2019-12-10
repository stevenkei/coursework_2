pipeline {
    agent any 
    stages {
        stage('Clean') { 
            steps {
                sh "exec server.js"
                sh "java server.js"
            }
        }
        stage('Test') { 
            steps {
                sh "mvn test" 
            }
        }
        stage('Deploy') { 
            steps {
                sh "mvn package" 
            }
        }
    }
}
