pipeline {
    agent any

    stages {

        stage('Test Webhook') {
            steps {
                echo 'Webhook triggered the pipeline successfully!'
            }
        }

        stage("Clean Workspace") {
            steps {
                cleanWs()
            }
        }

        stage('Checkout Code') {
            steps {
                sh 'git clone https://github.com/Saikiran121/ecommerce-microservices.git'
            }
        }
    }
}

