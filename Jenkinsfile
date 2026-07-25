pipeline {
    agent any
    
    environment {
        REPO_URL = "https://github.com/thenabeelhassan/resumegpt"
        BRANCH = "main"
        TARGET_DIR = "/var/www/resumegpt"
        GIT_CREDS = "github-pat"
    }
    
    stages {
        stage('Update Repository') {
            steps {
                script {
                    if (fileExists("${env.TARGET_DIR}/.git")) {
                        echo "Repository exists. Pulling latest changes..."
                        
                        dir(env.TARGET_DIR) {
                            sh "git pull origin main"
                        }
                    } else {
                        echo "Repository not found. Cloning..."

                        dir(env.TARGET_DIR) {
                            git(
                                branch: env.BRANCH,
                                credentialsId: env.GIT_CREDS,
                                url: env.REPO_URL
                            )
                        }
                    }
                }
            }
        }
    }
}
