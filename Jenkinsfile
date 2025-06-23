pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh '''
                echo "Building Docker image..."
                sudo -S docker build -t django-todo .
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                echo "Running Docker container..."
                sudo -S docker rm -f django-todo-container || true
                sudo -S docker run -d --name django-todo-container -p 8000:8000 django-todo
                '''
            }
        }
    }
}