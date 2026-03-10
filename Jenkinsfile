pipeline {
    agent any

    environment {
        DEV_SERVER = "3.110.121.192"
        STAGING_SERVER = "13.235.48.179"
        PROD_SERVER = "13.201.192.68"
        SSH_USER = "ubuntu"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/vaibhavbhuse42/Secure-CI-CD-Pipeline-with-Role-Based-Access-and-Environment-Promotion-Strategy.git'
            }
        }

        stage('Build') {
            steps {
                sh '''
                echo "Building application"
                mkdir -p build
                cp index.html build/
                '''
            }
        }

        stage('Unit Test') {
            steps {
                sh '''
                echo "Running sample tests"
                '''
            }
        }

        stage('Deploy to DEV') {
            steps {
                sshagent(['ubuntu']) {
                    sh """
                    scp -o StrictHostKeyChecking=no build/index.html $SSH_USER@$DEV_SERVER:/home/ubuntu/index.html
                    ssh -o StrictHostKeyChecking=no $SSH_USER@$DEV_SERVER "sudo mv /home/ubuntu/index.html /var/www/html/index.html"
                    """
                }
            }
        }

        stage('Deploy to STAGING') {
            steps {
                sshagent(['ubuntu']) {
                    sh """
                    scp -o StrictHostKeyChecking=no build/index.html $SSH_USER@$STAGING_SERVER:/home/ubuntu/index.html
                    ssh -o StrictHostKeyChecking=no $SSH_USER@$STAGING_SERVER "sudo mv /home/ubuntu/index.html /var/www/html/index.html"
                    """
                }
            }
        }

        stage('Production Approval') {
            steps {
                input message: "Approve Production Deployment?", ok: "Deploy"
            }
        }

        stage('Deploy to PRODUCTION') {
            steps {
                sshagent(['ubuntu']) {
                    sh """
                    scp -o StrictHostKeyChecking=no build/index.html $SSH_USER@$PROD_SERVER:/home/ubuntu/index.html
                    ssh -o StrictHostKeyChecking=no $SSH_USER@$PROD_SERVER "sudo mv /home/ubuntu/index.html /var/www/html/index.html"
                    """
                }
            }
        }
    }
}