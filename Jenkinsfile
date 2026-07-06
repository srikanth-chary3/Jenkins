pipeline {
    agent {
        node 'AGENT-1'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building'
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