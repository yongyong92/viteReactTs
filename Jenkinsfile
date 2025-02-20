pipeline {
    agent any

    environment {
        NODEJS_HOME = tool name: 'NodeJS 20.x', type: 'NodeJS'  // Jenkins에서 설정한 Node.js 버전
        PATH = "${NODEJS_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/yongyong92/viteReactTs.git'  // 깃 저장소 URL
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                // 배포 명령어
                sh 'rsync -avz dist/ devtest@192.168.0.29:22/path/to/deploy'
            }
        }
    }
}