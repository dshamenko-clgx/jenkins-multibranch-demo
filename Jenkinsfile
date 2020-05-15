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
                terraform.init(
                    color: true, 
                    backend_configs: [
                        'what',
                    ]
                )
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
