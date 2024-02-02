pipeline {
    agent any

    options {
        buildDiscarder(logRotator(artifactNumToKeepStr: '1', numToKeepStr: '5'))
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            when {
                expression { 
                    return env.BRANCH_NAME ==~ /^(feature|bugfix)\/.*$/
                }
            }
            steps {
                script {
                    echo "Building branch: ${env.BRANCH_NAME}"
                    // Add your build steps here
                }
            }
        }

        stage('Test') {
            when {
                expression { 
                    return env.BRANCH_NAME ==~ /^(feature|bugfix)\/.*$/
                }
            }
            steps {
                script {
                    echo "Testing branch: ${env.BRANCH_NAME}"
                    // Add your test steps here
                }
            }
        }

        stage('Deploy') {
            when {
                expression { 
                    return env.BRANCH_NAME == 'master'
                }
            }
            steps {
                script {
                    echo "Deploying branch: ${env.BRANCH_NAME}"
                    // Add your deployment steps here
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
    }
}
