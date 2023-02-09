pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building project...'
                sh 'make build'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing project...'
                sh 'make test'
            }
        }
        stage('Approval') {
            when {
                expression { env.APPROVE_EMAIL == 'true' }
            }
            steps {
                echo 'Sending approval email...'
                script {
                    def approval = input(
                        id: 'approval', 
                        message: 'Do you approve the release?', 
                        parameters: [
                            [$class: 'BooleanParameterDefinition', name: 'approve', type: 'Boolean', defaultValue: false, description: 'Check this box to approve']
                        ]
                    )
                    if (!approval.approve) {
                        error('Release approval not granted.')
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying project...'
                sh 'make deploy'
            }
        }
    }
}
