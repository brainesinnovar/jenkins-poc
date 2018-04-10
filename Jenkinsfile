repositoryUrl = "git@github.com:brainesinnovar/jenkins-poc.git"
branch = "master"

pipeline {
    agent any 

    stages {
        stage('Clone sources') {
            steps {
                git url: repositoryUrl, credentialsId: "1f147cba-c4fa-4719-86e3-1aee86c48521", branch: branch
            }
	}

	stage('Prepare') {
            steps {
                sh 'echo world'
            }
	}
    }
}
