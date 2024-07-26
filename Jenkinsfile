pipeline {
    agent any

    stages {    
        stage('Checkout') {
            steps {
                git 'https://github.com/jfrogdev/project-examples.git'
            }
        }
        stage('Run Dockerfile') {
            steps {
                script{
                    sh 'docker build -t chirag1212/java-app:latest .'
                    sh 'docker images'
                    sh 'docker push chirag1212/java-app:latest'
                }
            }
        }
        stage('Docker Deploy') {
            steps {
                script{
                    sh 'docker run -itd chirag1212/java-app:latest Sample-container /bin/bash'
                }
            }
        }
    }    
    post {
        success {
            echo 'Build and test succeeded!'
        }
        failure {
            echo 'Build or test failed!'
        }
    }
}