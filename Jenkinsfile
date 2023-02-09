pipeline {
    agent any
    stages {
        stage ('Build') {
            steps {
                echo 'Building the app'
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
        stage('Approval') {
            when {
                expression { env.APPROVE_EMAIL == 'true' }
            }
            steps {
                echo 'Sending approval email...'
                script {
                    // Send email to specific address
                    emailext body: "Please approve the release.",
                        subject: "Release Approval Request",
                        to: "vinod199733@gmail.com",
                        replyTo: "vinod199733@gmail.com",
                        mimeType: "text/html"
                    
                    // Wait for approval
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
        stage ('Deploy') {
            steps {
                echo 'Deploying the app'
            }
        }
    }
}
