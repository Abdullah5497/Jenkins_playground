pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'staging', 'production'],
            description: 'Select deployment environment'
        )
    }

    stages {

        stage('Build') {
            steps {
                echo "Building application..."
            }
        }

        stage('Deploy to Dev') {
            when {
                expression { params.ENVIRONMENT == 'dev' }
            }
            steps {
                echo "Deploying to DEV environment"
            }
        }

        stage('Deploy to Staging') {
            when {
                expression { params.ENVIRONMENT == 'staging' }
            }
            steps {
                echo "Deploying to STAGING environment"
            }
        }

        stage('Deploy to Production') {
            when {
                expression { params.ENVIRONMENT == 'production' }
            }
            steps {
                echo "🚀 Deploying to PRODUCTION environment"

                sh '''
                    echo "Running production deployment..."
                    # your production commands here
                    # kubectl apply -f deployment.yaml
                    # docker compose up -d
                '''
            }
        }
    }
}
