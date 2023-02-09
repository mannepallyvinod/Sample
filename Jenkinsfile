pipeline {
    agent any
    stages {
        stage ('Build') {
            steps {
                echo 'Building the app'
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
        stage ('Test') {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
                echo "Testing the app"
            }
        }
        stage ('Deploy') {
            steps {
                echo 'Deploying the app'
            }
        }
    }
}
