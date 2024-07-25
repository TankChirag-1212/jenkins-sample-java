pipeline {
    agent any

    tools {
        maven 'Maven_3.9.0' // Ensure this matches your Maven tool name
    }

    stages {    
        stage('Build') {
            steps {
                echo 'Building the Java application...'
                sh "mvn clean install"
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh "mvn test"
            }
    
        }

        stage('Deploy') {
            steps {
                sh "echo 'Deploying App.java..'"
                sh "cd src/main/java/com/example/"
                sh "javac App.java"
                sh "java App"
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