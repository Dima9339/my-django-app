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
        
        stage('Validate Configuration') {
            steps {
                sh 'ls -la'
                sh 'cat docker-compose.yml'
                sh 'cat Dockerfile'
                sh 'cat requirements.txt'
                echo '✓ All configuration files are present'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-django-app .'
                echo '✓ Docker image built successfully'
            }
        }
        
        stage('Deployment Ready') {
            steps {
                echo '✓ CI/CD Pipeline completed successfully!'
                echo 'Application is ready for deployment'
                echo 'Run manually: docker-compose up -d'
                echo 'Access at: http://localhost:8000'
            }
        }
    }
    
    post {
        success {
            echo '🎉 LABORATORY WORK COMPLETED SUCCESSFULLY!'
            echo 'All CI/CD stages demonstrated:'
            echo '- Repository cloning ✓'
            echo '- Configuration validation ✓' 
            echo '- Docker build ✓'
            echo '- Deployment readiness ✓'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
