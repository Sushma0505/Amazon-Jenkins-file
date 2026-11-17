
pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Clone') {
            steps {
                checkout scm
                echo 'Repository checkout completed'
            }
        }

        stage('Validate') {
            steps {
                script {
                    if (!fileExists('pom.xml')) {
                        error('pom.xml not found')
                    }
                }
                echo 'pom.xml found successfully'
            }
        }

        stage('Clean') {
            steps {
                echo 'Clean stage demonstration'
            }
        }

        stage('Compile') {
            steps {
                echo 'Compile stage demonstration'
            }
        }

        stage('Build') {
            steps {
                echo 'Build stage demonstration'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully'


        failure {
            echo 'Pipeline execution failed'
        }
    }
}
