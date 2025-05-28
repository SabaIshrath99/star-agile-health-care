pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/SabaIshrath99/star-agile-health-care.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
