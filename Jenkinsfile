pipeline {
    agent any

    tools {
        maven 'Maven_3.9.0' // Ensure this matches your Maven tool name
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git credentialsId: '85140349-35f6-4c74-9536-0c5df8f6e9c3', url: 'https://github.com/TankChirag-1212/jenkins-sample-java.git', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                // Build the project using Maven
                // script {
                //     withEnv(["PATH+MAVEN=${MAVEN_HOME}\\bin"]) {
                        // sh "echo $PATH"
                sh 'mvn clean install'
                    // }
                // }
            }
        }

        stage('Test') {
            steps {
                // Test the project using Maven
                // script {
                //     withEnv(["PATH+MAVEN=${MAVEN_HOME}\\bin"]) {
                sh 'mvn test'
                //     }
                // }
            }
        }

        stage('Archive Artifacts') {
            steps {
                // Archive the built artifacts
                archiveArtifacts artifacts: 'target/*.war', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
