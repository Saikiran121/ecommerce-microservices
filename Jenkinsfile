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

        stage('Show Java and Maven Version') {
            steps {
                sh '''
                    java --version
                    mvn --version
                '''
            }
        }

        stage('Build jar') {
            agent {
                docker {
                    image 'maven:3.9-eclipse-temurin-21'
                    args '-v /var/run/docker.sock:/var/run/docker.sock'
                }
            }
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

