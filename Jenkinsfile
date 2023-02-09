pipeline {
    agent any
    environment {
    NEW_VERSION = '1.3.0'
    }
    stages {
        stage ('Build') {
            steps {
                echo 'Building the app'
                echo "Building the ${NEW_VERSION} app"
            }
        }
        stage ('Test') {
            steps {
                echo "Testing the ${NEW_VERSION} app"
            }
        }
        stage ('Deploy') {
            steps {
                echo 'Deploying the app'
            }
        }
    }
}
