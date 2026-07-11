pipeline {
    agent {
        node {
            label "AGENT-1"
        }
    }
    stages {
        stage("Build") {
            steps {
                echo "Building"
            }
        }
        stage("Test") {
            steps {
                echo "Testing"
            }
        }
        stage("Deploy") {
            steps {
                echo "Deploying"
            }
        }
    }
    post {
        always {
            echo "I will say hello again"
            cleanWs()
        }
        success {
            echo "I will say hello, when it is a Success"
        }
        failure {
            echo "I will say hello, when it is a Failure"
        }
    }
}