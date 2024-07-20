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
        ME_CONFIG_MONGODB_SERVER="mongodb"
        ME_CONFIG_MONGODB_PORT="27017"
        ME_CONFIG_MONGODB_ENABLE_ADMIN="true"
        ME_CONFIG_MONGODB_ADMINUSERNAME="${env.ME_CONFIG_MONGODB_ADMINUSERNAME}" 
        ME_CONFIG_MONGODB_ADMINPASSWORD="${env.ME_CONFIG_MONGODB_ADMINPASSWORD}"
        ME_CONFIG_BASICAUTH_USERNAME="${env.ME_CONFIG_BASICAUTH_USERNAME}"
        ME_CONFIG_BASICAUTH_PASSWORD="${env.ME_CONFIG_BASICAUTH_PASSWORD}"
        REDIS_URL="redis://redis:6379"
        MYSQL_HOST="db"
        GOOGLE_CLOUD_PROJECT="${env.GOOGLE_CLOUD_PROJECT}"
        GCLOUD_STORAGE_BUCKET="${env.GCLOUD_STORAGE_BUCKET}"
        OPENAI_API_KEY="${env.OPENAI_API_KEY}"
        CLOVA_API_KEY="${env.CLOVA_API_KEY}"
        CLOVA_CLIENT_ID="${env.LOVA_CLIENT_ID}"
        JWT_SECRET="${env.JWT_SECRET}"
        REFRESH_TOKEN_SECRET="${env.REFRESH_TOKEN_SECRET}"
        TTS_API_KEY="${env.TTS_API_KEY}"
        ELEVENLABS_API_KEY="${env.ELEVENLABS_API_KEY}"
        GCP_TYPE="${env.GCP_TYPE}"
        GCP_PROJECT_ID="${env.GCP_PROJECT_ID}"
        GCP_PRIVATE_KEY_ID="${env.GCP_PRIVATE_KEY_ID}"
        GCP_PRIVATE_KEY="${env.GCP_PRIVATE_KEY}"
        GCP_CLIENT_EMAIL="${env.GCP_CLIENT_EMAIL}"
        GCP_CLIENT_ID="${env.GCP_CLIENT_ID}"
        GCP_AUTH_URI="${env.GCP_AUTH_URI}"
        GCP_TOKEN_URI="${env.GCP_TOKEN_URI}"
        GCP_AUTH_PROVIDER_X509_CERT_URL="${env.GCP_AUTH_PROVIDER_X509_CERT_URL}"
        GCP_CLIENT_X509_CERT_URL="${env.GCP_CLIENT_X509_CERT_URL}"
        GCP_UNIVERSE_DOMAIN="${env.GCP_UNIVERSE_DOMAIN}"
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