pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building project...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing project...'
            }
        }
        stage('Approval') {
            steps {
                echo 'Sending approval email...'
                script {
                    emailext body: "Please approve the release.",
                        subject: "Release Approval Request",
                        to: "vinod199733@gmail.com.com",
                        replyTo: "vinodkumarmannepally@gmail.com",
                        mimeType: "text/html"
                    def approve = params.approve
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
            }
        }
    }
}
