pipeline {
    agent any

    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('list files') {
            steps {
                sh 'ls -l target/*.war'
            }
        }
    }
}