pipeline {
    agent {
        docker { image 'mcr.microsoft.com/playwright:v1.20.2-focal' }
    }
    stages {
        stage('Run Tests') {
            parallel {
                stage('Firefox') {
                    steps {
                        sh 'TMP_WORK_DIR=$(mktemp -d) && ls $TMP_WORK_DIR && echo "data" > $TMP_WORK_DIR/data.txt'
                        sh 'npm install'
                        sh 'npx playwright screenshot --browser=firefox https://example.com ./out.png'
                        sh 'npx playwright test --project=firefox'
                    }
                }

                stage('Chromium') {
                    steps {
                        sh 'TMP_WORK_DIR=$(mktemp -d) && ls $TMP_WORK_DIR && echo "data" > $TMP_WORK_DIR/data.txt'
                        sh 'npm install'
                        sh 'npx playwright screenshot --browser=chromium https://example.com ./out.png'
                        sh 'npx playwright test --project=chromium'
                    }
                }

                stage('Firefox Headful') {
                    steps {
                        sh 'TMP_WORK_DIR=$(mktemp -d) && ls $TMP_WORK_DIR && echo "data" > $TMP_WORK_DIR/data.txt'
                        sh 'npm install'
                        sh 'xvfb-run -- npx playwright test --project="firefox headful"'
                    }
                }

                stage('Chromium Headful') {
                    steps {
                        sh 'TMP_WORK_DIR=$(mktemp -d) && ls $TMP_WORK_DIR && echo "data" > $TMP_WORK_DIR/data.txt'
                        sh 'npm install'
                        sh 'xvfb-run -- npx playwright test --project="chromium headful"'
                    }
                }
            }
        }
    }
}
