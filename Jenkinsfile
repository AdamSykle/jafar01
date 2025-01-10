pipeline {
    agent {
        docker { image 'maven:3.8.1-jdk-11' } // Пример для Java-проекта
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', credentialsId: 'github-token', url: 'https://github.com/AdamSykle/jafar01.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install' // Команда для сборки проекта
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test' // Команда для тестов
            }
        }
        stage('Docker Build & Push') {
            steps {
                script {
                    docker.build('your-image-name').push('your-repo/your-image-name')
                }
            }
        }
    }
}
