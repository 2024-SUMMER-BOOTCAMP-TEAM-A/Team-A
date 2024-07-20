pipeline {
    agent any
    
    environment {
        DOCKER_COMPOSE_FILE = 'docker-compose-deploy.yml'
        MYSQL_ROOT_PASSWORD = credentials('MYSQL_ROOT_PASSWORD')
        MYSQL_DATABASE = credentials('MYSQL_DATABASE')
        MYSQL_USER = credentials('MYSQL_USER')
        MYSQL_PASSWORD = credentials('MYSQL_PASSWORD')
        NODE_ENV = 'development'
        TZ = 'Asia/Seoul'
        DEPLOY_SERVER = 'angal2310@34.83.113.214'
        MONGO_INITDB_ROOT_USERNAME = credentials('MONGO_INITDB_ROOT_USERNAME')
        MONGO_INITDB_ROOT_PASSWORD = credentials('MONGO_INITDB_ROOT_PASSWORD')
        ME_CONFIG_MONGODB_ADMINUSERNAME = credentials('ME_CONFIG_MONGODB_ADMINUSERNAME')
        ME_CONFIG_MONGODB_ADMINPASSWORD = credentials('ME_CONFIG_MONGODB_ADMINPASSWORD')
        ME_CONFIG_BASICAUTH_USERNAME = credentials('ME_CONFIG_BASICAUTH_USERNAME')
        ME_CONFIG_BASICAUTH_PASSWORD = credentials('ME_CONFIG_BASICAUTH_PASSWORD')
        ME_CONFIG_MONGODB_ENABLE_ADMIN = 'true'
        OPENAI_API_KEY = credentials('OPENAI_API_KEY')
        CLOVA_API_KEY = credentials('CLOVA_API_KEY')
        CLOVA_CLIENT_ID = credentials('CLOVA_CLIENT_ID')
        JWT_SECRET = credentials('JWT_SECRET')
        REFRESH_TOKEN_SECRET = credentials('REFRESH_TOKEN_SECRET')
        TTS_API_KEY = credentials('TTS_API_KEY')
        ELEVENLABS_API_KEY = credentials('ELEVENLABS_API_KEY')
        GCP_TYPE = credentials('GCP_TYPE')
        GCP_PROJECT_ID = credentials('GCP_PROJECT_ID')
        GCP_PRIVATE_KEY_ID = credentials('GCP_PRIVATE_KEY_ID')
        GCP_PRIVATE_KEY = credentials('GCP_PRIVATE_KEY')
        GCP_CLIENT_EMAIL = credentials('GCP_CLIENT_EMAIL')
        GCP_CLIENT_ID = credentials('GCP_CLIENT_ID')
        GCP_AUTH_URI = credentials('GCP_AUTH_URI')
        GCP_TOKEN_URI = credentials('GCP_TOKEN_URI')
        GCP_AUTH_PROVIDER_X509_CERT_URL = credentials('GCP_AUTH_PROVIDER_X509_CERT_URL')
        GCP_CLIENT_X509_CERT_URL = credentials('GCP_CLIENT_X509_CERT_URL')
        GCP_UNIVERSE_DOMAIN = credentials('GCP_UNIVERSE_DOMAIN')
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
                        docker compose -f ${DOCKER_COMPOSE_FILE} down --remove-orphans&&
                        docker compose -f ${DOCKER_COMPOSE_FILE} pull &&
                        docker compose -f ${DOCKER_COMPOSE_FILE} up -d --remove-orphans'
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