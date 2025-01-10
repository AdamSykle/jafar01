pipeline {
    agent {
        docker { image 'python:3.12.2' } // Указывает на использование Docker-образа Python
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/AdamSykle/jafar01.git' // Замени на ссылку на свой репозиторий Git
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'pip install -r requirements.txt' // Установка зависимостей
            }
        }

        stage('Run tests') {
            steps {
                sh 'pytest' // Запуск тестов Python
            }
        }

        stage('Build Docker image') {
            steps {
                sh 'docker build -t my-python-app .' // Сборка Docker-образа
            }
        }

        stage('Run Docker container') {
            steps {
                sh 'docker run -d -p 5000:5000 my-python-app' // Запуск контейнера
            }
        }
    }
}
