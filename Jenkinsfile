pipeline {
    agent { label 'nodejs' }

    environment { APP_NAMESPACE = 'RHT_OCP4_DEV_USER-devsecops' }

    stages{

        stage('Test') {
            steps{
                sh "node test.js"
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    oc start-build greeting-devsecops \
                    --follow --wait -n ${APP_NAMESPACE}
                '''
            }
        }
    }
}
