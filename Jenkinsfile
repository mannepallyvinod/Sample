pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                echo "Building..."
            }
        }
        stage("Approval") {
            steps {
                script {
                    def approver = "vinod199733@gmail.com"
                    if (env.BRANCH_NAME == "master") {
                        mail to: approver,
                             subject: "Approval Needed: ${env.JOB_NAME}",
                             body: "Please approve this build: ${env.BUILD_URL}"
                    }
                }
            }
        }
        stage("Deploy") {
            when {
                expression { env.APPROVE == "yes" }
            }
            steps {
                echo "Deploying..."
            }
        }
    }
}
