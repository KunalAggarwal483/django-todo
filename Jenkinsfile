pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            options {
            timeout(time: 3, unit: 'MINUTES')
            }
            steps {
                sh '''
                echo "Building Docker image..."
                docker build -t django-todo .
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                echo "Running Docker container..."
                docker rm -f django-todo-container || true
                docker run -d --name django-todo-container -p 8000:8000 django-todo
                '''
            }
        }
    }

    post {
    always {
        sh 'docker image prune -f'
    }
    }
}