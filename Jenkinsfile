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

        // It makes the other or second job to wait until the first job finishes
        disableConcurrentBuilds()
    }

    //Parameters
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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
                        # used while checking the abort function in post build section
                        # sleep '20'
                    """
                }
            }
        }
        stage("Deploy") {
            Using input for manual intervention whether to approve the request or not while running the pipeline
            We can use this in defferent environments like UAT, Pre PROD, Staging and PROD environments
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
        // When is used to check the condition whether it is true it will continue or false it will stop pipeline
            // when {
            //     expression { "$params.DEPLOY" == "true" }
            // }

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