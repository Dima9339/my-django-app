pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'master', 
                credentialsId: 'github-credentials', 
                url: 'https://github.com/Dima9339/my-django-app.git'
            }
        }
        
        stage('Build and Deploy') {
            steps {
                sh 'docker-compose down'
                sh 'docker-compose build --no-cache'
                sh 'docker-compose up -d'
            }
        }
        
        stage('Run Migrations') {
            steps {
                sh 'docker-compose exec web python manage.py migrate'
            }
        }
        
        stage('Test Application') {
            steps {
                sh 'docker-compose exec web python manage.py test'
            }
        }
    }
    
    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }
        failure {
            echo 'CI/CD Pipeline failed.'
        }
    }
}