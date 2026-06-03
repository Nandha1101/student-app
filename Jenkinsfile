
pipeline {
    agent any

    environment {
        APP_NAME = "StudentApp"
    }

    parameters {
        string(
            name: 'BRANCH_NAME',
            defaultValue: 'main',
            description: 'Git branch to build'
        )
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: "${params.BRANCH_NAME}",
                url: 'https://github.com/Nandha1101/student-app.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }

    post {
        success {
            echo "${APP_NAME} build completed successfully!"
        }

        failure {
            echo "Build failed!"
        }
    }
}
