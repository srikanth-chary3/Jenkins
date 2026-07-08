pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building'
                echo 'Webhook Added'
            }
        }
		stage('Test') {
			steps {
				echo 'Testing'
			}
		}
		stage('Deploy') {
			steps {
				echo 'Deploying'
			}
		}
    }
}