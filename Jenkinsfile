pipeline {
    agent any

    stages {

        stage('Environment Setup') {
            steps {
                sh '''
                echo "creating virtual env..." 
                python3 -m venv venv
                . venv/bin/activate
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                echo "Installing Django dependencies..."
                venv/bin/pip install django
                '''
            }
        }

        stage('Build and Deploy') {
            steps {
                sh '''
                echo "Migrating servers"
                venv/bin/python manage.py migrate
                echo "starting server"
                nohup venv/bin/python manage.py runserver 0.0.0.0:8001 --noreload > /tmp/server.log 2>&1 &
                '''
            }
        }
    }
}