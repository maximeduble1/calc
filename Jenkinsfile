pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                git 'https://github.com/Maxiiminus2/calc.git'
                sh './mvnw clean compile verify sonar:sonar'
            }
        }
        stage('Test') {
            steps {
                sh './mvnw test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }
        stage('Publish') {
            steps {
                sh './mvnw package'
            }
            post {
                success {
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
