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
        DEPLOY_SERVER="angal2310@34.83.113.214"
        MONGO_INITDB_ROOT_USERNAME="${env.MONGO_INITDB_ROOT_USERNAME}"
        MONGO_INITDB_ROOT_PASSWORD="${env.MONGO_INITDB_ROOT_PASSWORD}"
        ME_CONFIG_MONGODB_ADMINUSERNAME="${env.ME_CONFIG_MONGODB_ADMINUSERNAME}" 
        ME_CONFIG_MONGODB_ADMINPASSWORD="${env.ME_CONFIG_MONGODB_ADMINPASSWORD}"
        ME_CONFIG_BASICAUTH_USERNAME="${env.ME_CONFIG_BASICAUTH_USERNAME}"
        ME_CONFIG_BASICAUTH_PASSWORD="${env.ME_CONFIG_BASICAUTH_PASSWORD}"
        ME_CONFIG_MONGODB_ENABLE_ADMIN=true
    }

    stages {
        stage('Checkout') {
            steps {
                cleanWs()
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
                        cd ~ &&
                        ls -al &&
                        docker compose -f ${DOCKER_COMPOSE_FILE} pull &&
                        docker compose -f ${DOCKER_COMPOSE_FILE} up -d'
                        """
                    }
                }
            }
        }
    }

    post {
        always {
            cleanWs(cleanWhenNotBuilt: false,
                    deleteDirs: true,
                    disableDeferredWipeout: true,
                    notFailBuild: true,
                    patterns: [[pattern: '.gitignore', type: 'INCLUDE'],
                            [pattern: '.propsfile', type: 'EXCLUDE']])
        }
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build or deployment failed.'
        }
    }
}