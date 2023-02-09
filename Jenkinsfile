pipeline {
    agent any
    environment {
    NEW_VERSION = '1.3.0'
    }
    stages {
        stage ('Build') {
            steps {
                echo 'Building the app'
                echo "Building the ${NEW_VERSION}"
            }
        }
        stage ('Test') {
            steps {
                echo 'Testing the app'
            }
        }
        stage ('Deploy') {
            steps {
                echo 'Deploying the app'
            }
        }
    }
}
