pipeline {

    agent {
        kubernetes {
            label 'insurance-platform'
            defaultContainer 'iac-tool'
        }
    }

    stages {

        stage('Prepare') {
            steps {
                echo '[INFO] Here will be our preparation steps'
            }
        }

        stage('TF Plan') {
            steps {
                echo '[INFO] Here will be our `terraform plan`'
            }
        }

        stage('TF Apply') {
            when {
                branch 'master'
            }
            steps {
                echo '[INFO] Here will be our `terraform apply`'
            }
        }
    }
}