pipeline {
    agent any
    environment {
        DOCKER_USER = 'sabaishrath99'
        DOCKER_PASS = 'Sabahks99@'   // **Note:** Ideally, store credentials securely in Jenkins, not hardcoded here.
    }
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
        stage('Dockerize') {
            steps {
                script {
                    // Login to Docker Hub
                    sh "echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin"
                    // Build and push image
                    sh 'docker build -t sabaishrath99/medicure:latest .'
                    sh 'docker push sabaishrath99/medicure:latest'
                }
            }
        }
        stage('Deploy') {
            steps {
                // Apply all k8s manifests inside k8s folder
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}

