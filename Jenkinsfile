pipeline {
    agent {
        docker { image 'mcr.microsoft.com/playwright:v1.20.2-focal' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'TMP_WORK_DIR=$(mktemp -d) && ls $TMP_WORK_DIR'
                sh 'npx playwright screenshot --browser=firefox https://example.com ./out.png'
            }
        }
    }
}
