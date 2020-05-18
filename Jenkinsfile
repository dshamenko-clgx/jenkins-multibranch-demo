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

    environment {
        TFPLAN = "${env.WORKSPACE}/terraform.plan"
    }

    stages {

        stage('Prepare') {
            steps {
                script {
                    terraform.init(
                        color: true, 
                        backend_configs: [
                            './demo.config',
                            ]
                        )
                }
            }
        }

        stage('TF Plan') {
            steps {
                echo '[INFO] Here will be our `terraform plan`'
                script {
                    terraform.plan(
                        color: true,
                        plan_file: env.TFPLAN
                    )
                }
            }
        }

        stage('TF Apply') {
            steps {
                echo '[INFO] Here will be our `terraform apply`'
                script {
                    terraform.apply(
                        color: true,
                        config_path: env.TFPLAN
                    )
                }
            }
        }
    }
}
