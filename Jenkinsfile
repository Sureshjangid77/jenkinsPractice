pipeline {
    agent any

    tools {
        maven 'Maven-3.9'
    }

    stages {

        stage('Build') {
            steps {
                dir('jenkins-demo') {
                    bat 'mvn clean compile'
                }
            }
        }

        stage('Test') {
            steps {
                dir('jenkins-demo') {
                    bat 'mvn test'
                }
            }
        }

        stage('Package') {
            steps {
                dir('jenkins-demo') {
                    bat 'mvn package'
                }
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'jenkins-demo/target/*.jar', fingerprint: true
            }
        }
        stage('Deploy') {
    steps {
        bat 'copy /Y jenkins-demo\\target\\*.jar C:\\Deployments\\jenkins-demo\\'
    }
}

        stage('JUnit Report') {
            steps {
                junit 'jenkins-demo/target/surefire-reports/*.xml'
            }
        }
    }
}