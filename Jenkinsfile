pipeline {
    agent{ label 'devops-01-esa'}

    stages {
        stage('Pull Source Code') {
            steps {
                git branch: 'main', url: 'https://github.com/mastirt/laravel-blog.git'
            }
        }
        stage('Testing Application') {
            steps {
                echo 'Testing Application'
            }
        }
        stage('Build Container Image') {
            steps {
                echo 'Build Container Image'
            }
        }
        stage('Deploy Container Application') {
            steps {
                echo 'Deploy Container Application'
            }
        }
        stage('Publish Container Image') {
            steps {
                echo 'Publish Container Image'
            }
        }
    }
}
