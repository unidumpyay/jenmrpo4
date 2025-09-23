pipeline {
    agent any

    environment {
        MY_GLOBAL_VARIABLE = 'HelloJenkins'
    }

    stages {
        stage('Build') {
            steps {
                echo "Сборка приложения..."
                echo "Глобальная переменная: ${env.MY_GLOBAL_VARIABLE}"
            }
        }
        stage('Test') {
            steps {
                echo "Тестирование приложения..."
                echo "Используем переменную: ${env.MY_GLOBAL_VARIABLE}"
            }
        }
        stage('Deploy') {
            steps {
                echo "Развёртывание приложения..."
                echo "Переменная доступна здесь: ${env.MY_GLOBAL_VARIABLE}"
            }
        }
    }

    post {
        always {
            echo "Очистка рабочей области..."
            deleteDir()
        }
        success {
            echo "Сборка прошла успешно!"
        }
        failure {
            echo "Сборка завершилась с ошибкой!"
        }
    }
}
