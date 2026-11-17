
pipeline {
    agent any

    parameters {
        booleanParam(
            name: 'FORCE_FAILURE',
            defaultValue: false,
            description: 'Select to test failure email'
        )
    }

    stages {
        stage('Clone') {
            steps {
                echo 'Clone stage completed'
            }
        }

        stage('Clean') {
            steps {
                echo 'Clean stage completed'
            }
        }

        stage('Validate') {
            steps {
                echo 'Validation successful'
            }
        }

        stage('Compile') {
            steps {
                echo 'Compilation stage completed'
            }
        }

        stage('Build') {
            steps {
                script {
                    if (params.FORCE_FAILURE) {
                        error('Intentional build failure')
                    }
                    echo 'Build completed successfully'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline SUCCESS'

            emailext(
                to: 'sushmasus2021@gmail.com',
                subject: "SUCCESS - ${env.JOB_NAME}",
                body: """Hello Team,

Jenkins Pipeline build completed successfully.

Job: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Status: SUCCESS
Build URL: ${env.BUILD_URL}

Regards,
Jenkins
"""
            )
        }

        failure {
            echo 'Pipeline FAILURE'

            emailext(
                to: 'sushmasus2021@gmail.com',
                subject: "FAILURE - ${env.JOB_NAME}",
                body: """Hello Team,

Jenkins Pipeline build failed.

Job: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Status: FAILURE
Build URL: ${env.BUILD_URL}

Regards,
Jenkins
"""
            )
        }
    }
}
