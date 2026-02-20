pipeline {
    agent { label 'windows' }

    environment {
        DEPLOY_DIR = "C:\\inetpub\\wwwroot\\headphone"
    }

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/1MRCV/headphone.git', branch: 'main'
            }
        }

        stage('Deploy to IIS') {
            steps {
                bat '''
                if not exist "%DEPLOY_DIR%" (
                    mkdir "%DEPLOY_DIR%"
                )
                xcopy /Y /E "%WORKSPACE%\\*" "%DEPLOY_DIR%\\"
                '''
            }
        }
    }
}
