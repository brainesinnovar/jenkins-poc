repositoryUrl = "git@github.com:brainesinnovar/jenkins-poc.git"
branch = "master"

pipeline {
    agent any 

    stages {
        stage('Clone Source') {
            steps {
                git url: repositoryUrl, credentialsId: "1f147cba-c4fa-4719-86e3-1aee86c48521", branch: branch
            }
        }

        stage('Prepare Application') {
            steps {
                sh 'echo "Copy parameters.yml"'
                sh 'echo "Get composer.phar"'
                sh 'echo "Remove app_dev.php and config.php"'
                sh 'echo "Set permissions (if needed)"'
                sh 'echo "Run composer install"'
                sh 'echo "Run assets install (not symlink)"'
                sh 'echo "Run fos router generate"'
            }
        }
        
        stage('Check Syntax') {
            steps {
                sh 'echo "Run PHP Parallel Lint: bin/parallel-lint"'
                /* https://github.com/JakubOnderka/PHP-Parallel-Lint */
            }
        }
        
        stage('Test') {
            steps {
                sh 'echo "Run PHPUnit: bin/phpunit"'
                /* https://phpunit.de/ */
                
                sh 'echo "Run SonarQ"'
            }
        }
        
        stage('Check Style') {
            steps {
                sh 'echo "Run PHP_CodeSniffer: bin/phpcs"'
                /* https://github.com/squizlabs/PHP_CodeSniffer */
            }
        }
        
        stage('Lines of Code') {
            steps { 
                sh 'echo "Run PHP lines of code: bin/phploc"'
                /* https://github.com/sebastianbergmann/phploc */
            }
        }
        
        stage('Copy Paste Detection') {
            steps {
                sh 'echo "Run PHP Copy Paste Detector: bin/phpcpd"'
                /* https://github.com/sebastianbergmann/phpcpd */
            }
        }
        
        /* -- SLOW */
        stage('Mess Detection') {
            steps {
                sh 'echo "Run PHP Mess Detector: bin/phpmd"'
                /* https://phpmd.org/ */
            }
        }
        
        /* -- SLOW */
        stage('Software Metrics') {
            steps { 
                sh 'echo "Run PHP Depend: bin/pdepend"'
                /* https://pdepend.org/ */
            }
        }
        
        stage('Generate Documentation') {
            steps { 
                sh 'echo "run bin/phpdox"'
                /* http://phpdox.de/ */
            }
        }
        
        stage('Generate php metrics') {
            steps {                
                sh 'echo "run bin/phpmetrics"' 
                /* https://www.phpmetrics.org/ */
            }
        }
        
        stage('Create Artifact') {
            steps {
                sh 'echo "create tar.gz of the build dir"' 
            }
        }
    }
}
