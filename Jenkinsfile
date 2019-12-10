pipeline {
    agent any 
    stages {
        stage('Clean') { 
            steps {
                sh "javac server.js"
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
