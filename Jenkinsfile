pipeline {

    agent {
        kubernetes {
            label 'insurance-platform'
            defaultContainer 'iac-tool'
        }
    }

    options {
        ansiColor('xterm')
    }

    stages {

        stage('Prepare') {
            steps {
                script {
                    terraform.init(
                        color: true, 
                        backend_configs: [
                            'what',
                            'heck'
                            ]
                        )
                } 
            }
        }

        stage('TF Plan') {
            steps {
                echo '[INFO] Here will be our `terraform plan`'
                echo '[DEBUG] verbose of `terraform plan`'
                echo '[DEBUG] added'
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
