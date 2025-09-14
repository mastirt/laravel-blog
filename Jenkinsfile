pipeline {
    agent{ label 'devops-01-esa'}

    stages {
        stage('Pull Source Code') {
            steps {
                git branch: 'main', url: 'https://github.com/mastirt/laravel-blog.git'
            }
        }
        stage('Copy env Variable') {
            steps {
                sh '''
                cp /usr/share/nginx/html/laravel-blog/.env .env
                '''
            }
        }
        stage('Code Quality Analysis') {
            steps {
                sh '''
                sonar-scanner \
                -Dsonar.projectKey=laravel-blog \
                -Dsonar.sources=. \
                -Dsonar.host.url=http://172.23.5.42:9000 \
                -Dsonar.token=sqp_f5f59484950294a6765dce8054cbed5c6b020498
                '''
            }
        }
        stage('Build Container Image') {
            steps {
                sh '''
                docker compose build
                '''
            }
        }
        stage('Deploy Container Application') {
            steps {
                sh '''
                docker compose up -d
                '''
            }
        }
        stage('Publish Container Image') {
            steps {
                sh '''
                docker compose push
                '''
            }
        }
    }
}
