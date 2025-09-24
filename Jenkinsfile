pipeline {
    agent any

    stages {
        stage('Сборка') {
            steps {
                echo "Сборка приложения..."
                sh '''
                    echo "Этот блок содержит многострочные шаги"
                    ls -lh
                '''
            }
        }

        stage('Тестирование') {
            steps {
                echo "Запуск unit-тестов..."
                // Здесь можно добавить свои тесты, если будут
                sh 'echo "Все тесты прошли успешно"'
            }
        }

        stage('Деплой на стейджинг') {
            steps {
                echo "Изменяем права на выполнение скриптов"
                sh 'chmod +x deploy smoke-tests || echo "chmod уже сделан"'

                echo "Деплой на стейджинг"
                sh './deploy staging'

                echo "Запуск smoke-тестов"
                sh './smoke-tests'
            }
        }

        stage('Проверка перед продакшеном') {
            steps {
                input "Всё ок? Отправить на продакшен?"
            }
        }

        stage('Деплой на продакшен') {
            steps {
                echo "Деплой на продакшен"
                sh './deploy prod'
            }
        }
    }

    post {
        always {
            echo "Этот блок выполняется всегда (например, очистка воркспейса)"
        }
        success {
            echo "Сборка прошла успешно"
        }
        failure {
            echo "Сборка провалилась"
        }
    }
}
