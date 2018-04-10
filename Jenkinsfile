repositoryUrl = "ssh://git@github.com:brainesinnovar/jenkins-poc.git"
branch = "master"

pipeline {
    agent any 

    stages {
        stage('Clone sources') {
            steps {
                sh 'echo hello'
            }
	}

	stage('Prepare') {
            steps {
                sh 'echo world'
            }
	}
    }
}
