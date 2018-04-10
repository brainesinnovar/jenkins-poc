repositoryUrl = "git@github.com:brainesinnovar/jenkins-poc.git"
branch = "master"

pipeline {
    agent any 

    stages {
        stage('Clone sources') {
            steps {
                git url: repositoryUrl, credentialsId: "git-credentials", branch: branch
            }
	}

	stage('Prepare') {
            steps {
                sh 'echo world'
            }
	}
    }
}
