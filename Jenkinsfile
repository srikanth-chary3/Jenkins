// This is said to be Pre-Build section
pipeline {
    agent {
        node {
            label "AGENT-1"
        }
    }

    // Environment Variables
    environment {
        COURSE="Jenkins"
        DURATION="14 Hrs"
    }

    // Options
    options {
        timeout (time: 10, unit: 'SECONDS')
    }

// This is said to be Build section
    stages {
        stage("Build") {
            steps {
                echo "Building"
                script {
                    sh """
                        echo
                        echo "Hello from the Script..!"
                        echo
                        echo $COURSE
                        echo $DURATION
                    """
                }
            }
        }
        stage("Test") {
            steps {
                echo "Testing"
                script {
                    sh """
                        echo
                        echo "Hello from the Script..!"
                        echo
                    """
                }
            }
        }
        stage("Deploy") {
            steps {
                echo "Deploying"
                script {
                    sh """
                        echo
                        echo "Hello from the Script..!"
                        echo
                    """
                }
            }
        }
    }

// This is said to be Post-Build section
    post {
        always {
            echo "I will say hello again"
            // It cleans the workspace
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