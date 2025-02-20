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
            }
        }

        stage('Deploy') {
            steps {
                sh 'npm run dev'
            /*
                script {
                    def remoteUser = "devtest"
                    def remoteHost = "192.168.0.29"
                    def remotePath = "/var/www/vietReacTs/"
                    def sshPort = "22"

                    // 서버에 파일 배포
                    //sh "rsync -avz -e 'ssh -o StrictHostKeyChecking=no -p 22' dist/ devtest@192.168.0.29:/var/www/vietReacTs/"
                    sh "rsync -avz -e 'ssh -i /var/lib/jenkins/.ssh/yytest -o StrictHostKeyChecking=no -p 22' dist/ devtest@192.168.0.29:/var/www/vietReacTs/"


                    // 서버에서 애플리케이션 재시작
                    sh "ssh -p 22 devtest@192.168.0.29 'pm2 restart vietReacTs'"
                }
            */
            }
        }
    }
}