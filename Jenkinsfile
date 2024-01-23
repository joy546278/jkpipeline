pipeline {
    agent any

    environment {
        GIT_REPO_URL = 'https://github.com/joy546278/jkpipeline.git'
        NGINX_PATH = 'D:\\nginx\\nginx-1.25.3\\nginx-1.25.3\\html_docs'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Use the checkout step to clone the Git repository
                    checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'b61935a8-3cac-4281-92a4-a2b73d883d1f', url: 'https://github.com/joy546278/jkpipeline.git']])
                }
            }
        }

        stage('Deploy to Nginx') {
            steps {
                script {
                    // Using the Jenkins workspace variable to reference files
                    bat 'xcopy /y "C:\\Users\\ASUS\\Desktop\\DNSJ\\index.html" "%NGINX_PATH%"'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! You can add additional steps here.'
        }
        failure {
            echo 'Pipeline failed! You may want to take some actions.'
        }
    }
}
