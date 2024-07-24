pipeline {
    agent any
    
    environment {
        DOCKER_COMPOSE_FILE = 'docker-compose-deploy.yml'
        MYSQL_ROOT_PASSWORD="${MYSQL_ROOT_PASSWORD}"
        MYSQL_DATABASE="${MYSQL_DATABASE}"
        MYSQL_USER="${MYSQL_USER}"
        MYSQL_PASSWORD="${MYSQL_PASSWORD}"
        NODE_ENV="${NODE_ENV}"
        TZ="${TZ}"
        DEPLOY_SERVER="angal2310@34.83.113.214"
        MONGO_INITDB_ROOT_USERNAME="${MONGO_INITDB_ROOT_USERNAME}"
        MONGO_INITDB_ROOT_PASSWORD="${MONGO_INITDB_ROOT_PASSWORD}"
        ME_CONFIG_MONGODB_SERVER="mongodb"
        ME_CONFIG_MONGODB_PORT="27017"
        ME_CONFIG_MONGODB_ENABLE_ADMIN="true"
        MONGOEXPRESS_LOGIN="${MONGOEXPRESS_LOGIN}"
        MONGOEXPRESS_PASSWORD="${MONGOEXPRESS_PASSWORD}"
        REDIS_URL="redis://redis:6379"
        MYSQL_HOST="db"
        GOOGLE_CLOUD_PROJECT="${GOOGLE_CLOUD_PROJECT}"
        GCLOUD_STORAGE_BUCKET="${GCLOUD_STORAGE_BUCKET}"
        OPENAI_API_KEY="${OPENAI_API_KEY}"
        CLOVA_API_KEY="${CLOVA_API_KEY}"
        CLOVA_CLIENT_ID="${CLOVA_CLIENT_ID}"
        JWT_SECRET="${JWT_SECRET}"
        REFRESH_TOKEN_SECRET="${REFRESH_TOKEN_SECRET}"
        ELEVENLABS_API_KEY="${ELEVENLABS_API_KEY}"
        GCP_TYPE="${GCP_TYPE}"
        GCP_PROJECT_ID="${GCP_PROJECT_ID}"
        GCP_PRIVATE_KEY_ID="${GCP_PRIVATE_KEY_ID}"
        GCP_PRIVATE_KEY="${GCP_PRIVATE_KEY}"
        GCP_CLIENT_EMAIL="${GCP_CLIENT_EMAIL}"
        GCP_AUTH_URI="${GCP_AUTH_URI}"
        GCP_TOKEN_URI="${GCP_TOKEN_URI}"
        GCP_AUTH_PROVIDER_X509_CERT_URL="${GCP_AUTH_PROVIDER_X509_CERT_URL}"
        GCP_CLIENT_X509_CERT_URL="${GCP_CLIENT_X509_CERT_URL}"
        GCP_UNIVERSE_DOMAIN="${GCP_UNIVERSE_DOMAIN}"
        MONGODB_DOCKER_URL="${MONGODB_DOCKER_URL}"
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
                        scp -o StrictHostKeyChecking=no TEAM-A ${DEPLOY_SERVER}:~/TEAM-A
                        ssh -o StrictHostKeyChecking=no ${DEPLOY_SERVER} '
                        export MYSQL_ROOT_PASSWORD="${MYSQL_ROOT_PASSWORD}" &&
                        export MYSQL_DATABASE="${MYSQL_DATABASE}" &&
                        export MYSQL_USER="${MYSQL_USER}" &&
                        export MYSQL_PASSWORD="${MYSQL_PASSWORD}" &&
                        export NODE_ENV="${NODE_ENV}" &&
                        export TZ="${TZ}" &&
                        export MONGO_INITDB_ROOT_USERNAME="${MONGO_INITDB_ROOT_USERNAME}" &&
                        export MONGO_INITDB_ROOT_PASSWORD="${MONGO_INITDB_ROOT_PASSWORD}" &&
                        export MONGOEXPRESS_LOGIN="${MONGOEXPRESS_LOGIN}" &&
                        export MONGOEXPRESS_PASSWORD="${MONGOEXPRESS_PASSWORD}" &&
                        export REDIS_URL="redis://redis:6379" &&
                        export MYSQL_HOST="db" &&
                        export GOOGLE_CLOUD_PROJECT="${GOOGLE_CLOUD_PROJECT}" &&
                        export GCLOUD_STORAGE_BUCKET="${GCLOUD_STORAGE_BUCKET}" &&
                        export OPENAI_API_KEY="${OPENAI_API_KEY}" &&
                        export CLOVA_API_KEY="${CLOVA_API_KEY}" &&
                        export CLOVA_CLIENT_ID="${CLOVA_CLIENT_ID}" &&
                        export JWT_SECRET="${JWT_SECRET}" &&
                        export REFRESH_TOKEN_SECRET="${REFRESH_TOKEN_SECRET}" &&
                        export ELEVENLABS_API_KEY="${ELEVENLABS_API_KEY}" &&
                        export GCP_TYPE="${GCP_TYPE}" &&
                        export GCP_PROJECT_ID="${GCP_PROJECT_ID}" &&
                        export GCP_PRIVATE_KEY_ID="${GCP_PRIVATE_KEY_ID}" &&
                        export GCP_PRIVATE_KEY="${GCP_PRIVATE_KEY}" &&
                        export GCP_CLIENT_EMAIL="${GCP_CLIENT_EMAIL}" &&
                        export GCP_AUTH_URI="${GCP_AUTH_URI}" &&
                        export GCP_TOKEN_URI="${GCP_TOKEN_URI}" &&
                        export GCP_AUTH_PROVIDER_X509_CERT_URL="${GCP_AUTH_PROVIDER_X509_CERT_URL}" &&
                        export GCP_CLIENT_X509_CERT_URL="${GCP_CLIENT_X509_CERT_URL}" &&
                        export GCP_UNIVERSE_DOMAIN="${GCP_UNIVERSE_DOMAIN}" &&
                        export MONGODB_DOCKER_URL="${MONGODB_DOCKER_URL}" &&
                        cd ~ &&
                        ls -al &&
                        docker compose -f TEAM-A/${DOCKER_COMPOSE_FILE} down --remove-orphans &&
                        docker compose -f TEAM-A/${DOCKER_COMPOSE_FILE} pull &&
                        docker compose -f TEAM-A/${DOCKER_COMPOSE_FILE} up -d'
                        rm r -f TEAM-A
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