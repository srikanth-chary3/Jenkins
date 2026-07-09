pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment {
        Name = "Srikanth"
    }
    options {
        timeout(time: 10, unit: SECONDS)
        disableConcurrentBuilds()
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
