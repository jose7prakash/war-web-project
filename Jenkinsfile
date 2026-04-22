pipeline {
    environment {
        PATH = "/opt/maven/bin:${env.PATH}"
    }
    Stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                environment {
                    scannerHome = tool 'jp-sonar-scanner'
                }
                steps {
                    withSonarQubeEnv('jp-sonar') {
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }

               }
        }
    }
}
