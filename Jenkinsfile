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

        stage('Build jar') {
            steps {
                dir('ecommerce-microservices/order-service') {
                    sh 'mvn -B -DskipTests clean package'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('ecommerce-microservices/order-service') {
                    sh 'docker build -t saikiran8050/order-service:0.15 .'
                }
            }
        }
    }
}

