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
        stage('SonarQube Analysis') {
            
                environment {
                    scannerHome = tool 'jp-sonar-scanner'
                }
                steps {
                    withSonarQubeEnv('jpsqser') {
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }

               }
        }
    }

