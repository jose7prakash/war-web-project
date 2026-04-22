pipeline {
    agent any   
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('Build') {
            steps {
                echo 'starting build'
                sh "mvn clean deploy -Dmaven.test.skip=true"
                echo 'Build and Deploy successful'
            }
            stage('test') {
                steps {
                    echo 'start testing'
                    sh 'mvn surefire-report:report'
                    echo 'end testing'
                                    }
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

