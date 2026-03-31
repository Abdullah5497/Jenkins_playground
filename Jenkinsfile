pipeline {
    agent any

    parameters {
        choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Choose environment')
        string(name: 'VERSION', defaultValue: '1.0', description: 'App version')
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Branch: ${env.BRANCH_NAME}"
                echo "Environment: ${params.ENV}"
                echo "Version: ${params.VERSION}"
            }
        }

        stage('Build') {
            when {
                expression { params.ENV == 'dev' }
            }
            steps {
                echo "Building for DEV..."
            }
        }

        stage('Deploy') {
            when {
                expression { params.ENV == 'prod' }
            }
            steps {
                echo "Deploying to PROD..."
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }

        success {
            echo "Build SUCCESS ✅"
        }

        failure {
            echo "Build FAILED ❌"
        }

        unstable {
            echo "Build UNSTABLE ⚠️"
        }
    }
}
