pipeline {
    agent any
    parameters {
        choice(name: 'version', choices: ['1.1.0', '1.2.0', '1.3.0'], description: 'Test the version')
        booleanparam(name: 'executeTests', defaultValue: 'true', description: '')
    }
    stages {
        stage ('Build') {
            steps {
                echo 'Building the app'
                echo "Building the ${version} app"
            }
        }
        stage ('Test') {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
                echo "Testing the ${NEW_VERSION} app"
            }
        }
        stage ('Deploy') {
            steps {
                echo 'Deploying the app'
                echo "Deploying the version ${version}"
            }
        }
    }
}
