pipeline {
    agent any

    stages {

        stage('Environment Setup') {
            steps {
                sh '''
                #!/bin/bash
                echo "creating virtual env..." 
                python3 -m venv venv
                source venv/bin/activate
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                echo "Installing Django dependencies..."
                pip install django
                '''
            }
        }

        stage('Build and Deploy') {
            steps {
                sh '''
                echo "Migrating servers"
                python manage.py migrate
                echo "starting server"
                python manage.py runserver 0.0.0.0:8000 > /tmp/server.log 2>&1
                '''
            }
        }
    }
}