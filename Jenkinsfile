pipeline {
    agent any

    tools {
        maven 'M3'
    }

    stages {
       stage('Checkout') {
           steps {
               echo 'Checking out source code...'
               git branch: 'main', url: 'https://github.com/Vistaar07/devops_exam'
           }
       }

       stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! Archiving artifacts...'
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}