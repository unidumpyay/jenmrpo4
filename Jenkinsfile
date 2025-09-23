pipeline {
    agent any
    environment {
        GOOGLE_KEY = credentials('GOOGLE-ACCESS-KEY-ID')
    }
    stages {
        stage('Build') {
            steps {
                echo "Сборка приложения..."
            }
        }
        stage('Test') {
            steps {
                echo "Тестирование приложения..."
            }
        }
        stage('Deploy') {
            steps {
                echo "Развёртывание приложения..."
                echo "Используем секретный ключ: ${env.GOOGLE_KEY}"
            }
        }
    }
    post {
        always {
            deleteDir()
        }
    }
}
