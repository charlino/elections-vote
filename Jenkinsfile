pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/charlino/elections-vote.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t elections-vote-app .'
            }
        }
        stage('Deploy Container') {
            steps {
                sh 'docker run -d --name elections-vote-app --network front-tier --network back-tier -p 5000:80 elections-vote-app'
            }
        }
    }
}
