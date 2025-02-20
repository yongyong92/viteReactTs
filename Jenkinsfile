pipeline {
    agent any
/*
    environment {
        NODEJS_HOME = tool name: 'NodeJS 20.x', type: 'NodeJS'  // Jenkins에서 설정한 Node.js 버전
        PATH = "${NODEJS_HOME}/bin:${env.PATH}"
    }
*/
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', credentialsId: 'yytest', url:'https://github.com/yongyong92/viteReactTs.git'  // 깃 저장소 URL
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
                sh 'pwd'
            }
        }
    }

    post {
        success {
                sh 'pwd'
                //sh 'cd'
                //sh 'npm run dev &'
        }
    }
}