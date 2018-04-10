repositoryUrl = "git@github.com:brainesinnovar/jenkins-poc.git"
branch = "master"

pipeline {
    agent any 

    stages {
        stage('Clone source') {
            steps {
                git url: repositoryUrl, credentialsId: "1f147cba-c4fa-4719-86e3-1aee86c48521", branch: branch
            }
        }

        stage('Prepare') {
            steps {
                sh 'ehco "Copy parameters.yml"'
                sh 'ehco "Get composer.phar"'
                sh 'ehco "Set permissions (if needed)"'
                sh 'ehco "Run composer install"'
            }
        }
        
        stage('PHP Syntax check') {
            steps {
                sh 'echo "run bin/parallel-lint"'
            }
        }
        
        stage('Test') {
            steps {
                sh 'echo "run bin/phpunit"'
                sh 'echo "run SonarQ"'
            }
        }
        
        stage('Checkstyle') {
            steps {
                sh 'echo "run bin/phpcs'
            }
        }
        
        stage('Lines of Code') {
            steps { 
                sh 'echo "bin/phploc"'
            }
        }
        
        stage('Copy paste detection') {
            steps {
                sh 'echo "run bin/phpcpd"'
            }
        }
        
        /* -- SLOW */
        stage('Mess detection') {
            steps {
                sh 'echo run bin/phpmd'
            }
        }
        
        /* -- SLOW */
        stage('Software metrics') {
            steps { 
                sh 'echo run bin/pdepend'
            }
        }
        
        stage('Generate documentation') {
            steps { 
                sh 'echo "run bin/phpdox"'
            }
        }
        
        stage('Generate php metrics') {
            steps {
                sh 'echo "run bin/phpmetrics"'
            }
        }
    }
}
