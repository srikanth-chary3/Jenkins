// This is said to be Pre-Build section
pipeline {
    // Using a default agent
    agent any
    // agent {
    //     node {
    //         label "AGENT-1"
    //     }
    // }

// This is said to be Build section
    stages {
        stage("Build") {
            steps {
                //echo "Building"
                script {
                    sh """
                        echo
                        echo "Hello from the Script..!
                        echo
                    """
                }
            }
        }
        stage("Test") {
            steps {
                //echo "Testing"
                script {
                    sh """
                        echo
                        echo "Hello from the Script..!
                        echo
                    """
                }
            }
        }
        stage("Deploy") {
            steps {
                //echo "Deploying"
                script {
                    sh """
                        echo
                        echo "Hello from the Script..!
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
            //cleanWs()
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