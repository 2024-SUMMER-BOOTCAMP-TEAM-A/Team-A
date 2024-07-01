pipeline {
    agent any
    
    environment {
        DOCKER_COMPOSE_FILE = 'docker-compose-deploy.yml'
        MYSQL_ROOT_PASSWORD="${env.MYSQL_ROOT_PASSWORD}"
        MYSQL_DATABASE="${env.MYSQL_DATABASE}"
        MYSQL_USER="${env.MYSQL_USER}"
        MYSQL_PASSWORD="${env.MYSQL_PASSWORD}"
        NODE_ENV="${env.NODE_ENV}"
        TZ="${env.TZ}"
        DEPLOY_SERVER="34.83.113.214"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/2024-SUMMER-BOOTCAMP-TEAM-A/Team-A.git'
            }
        }

        stage('Test') {
            steps {
                script {
                    sh "docker --version"
                    sh "docker compose --version"
                    sh "echo hello world!"
                }
            }
        }

        stage('Deploy') {
            when {
                anyOf {
                    branch 'main'
                    branch 'master'
                }
            }
            steps {
                script {
                    sshagent(['deploy-ssh']) {
                        sh """
                        scp -o StrictHostKeyChecking=no ${DOCKER_COMPOSE_FILE} ${DEPLOY_SERVER}:~/${DOCKER_COMPOSE_FILE}
                        ssh -o StrictHostKeyChecking=no ${DEPLOY_SERVER} '
                        docker-compose pull &&
                        docker-compose up -d'
                        """
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build or deployment failed.'
        }
    }
}