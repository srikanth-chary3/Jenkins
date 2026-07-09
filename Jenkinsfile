pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }

    // There variables are global variable and we can access them accross the jenkinsfile anywhrere in pipeline
    environment {
        Name = "Srikanth"
    }

    // Options are used for special purpose
    options {
        timeout(time: 10, unit: SECONDS)
        disableConcurrentBuilds()
    }

// Parameters are like user inputs while runngin the pipeline, we need to select the options from these parameters
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages {
        stage ("Hello") {
            steps {
                sh "env"
                echo "${env.Name}"
            }
        }
        stage ("Script") {
            steps {
                script {
                    sh """
                    cat /etc/os-release
                    sleep 10
                    """
                }
            }
        stage ("Deployment") {
            // This input section is used like parameters but it is mostly used with when condition etc...
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }

            // When is a conditional function, it is used in the pipeline whether the condition meets or not while running the pipeline
            when {
                expression { "$params.DEPLOY" == "true" } // Here we are checking the condition with DEPLOY param
            }
            steps {
                script{
                    sh """
                    echo "Building"
                    echo $COURSE
                    sleep 10
                    env

                    echo "Hello ${params.PERSON}"
                    echo "Biography: ${params.BIOGRAPHY}"
                    echo "Toggle: ${params.DEPLOY}"
                    echo "Choice: ${params.CHOICE}"
                    echo "Password: ${params.PASSWORD}"
                    """
                }
            }
        stage('Test') {
            steps {
                script{
                    sh """
                        echo "Building"
                    """
                }
            }
        }
    }
    post {
        always {
            echo "I always print this line at the end of the Pipeline"
            cleanWs()
        }
        success {
            echo "I Will print if the pipeline succeeds"
        }
        failure {
            echo "I will print if the pipeline fails"
        }
        aborted {
            echo "I will print if the pipeline is aborted"
        }
    }
}
