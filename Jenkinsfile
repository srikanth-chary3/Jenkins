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
                script {
                    sh """
                        echo "Hello from the Script..!
                    """
                }
            }
        }
        stage("Test") {
            steps {
                echo "Testing"
                script {
                    sh """
                        echo "Hello from the Script..!
                    """
                }
            }
        }
        stage("Deploy") {
            steps {
                echo "Deploying"
                script {
                    sh """
                        echo "Hello from the Script..!
                    """
                }
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
        aborted {
            echo "I will say hello, when it is Aborted or Interrupted"
        }
    }
}