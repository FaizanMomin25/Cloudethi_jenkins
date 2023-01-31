pipeline {
    agent any
    environment {
        dev_acc_id = '1545788888778'
        qa_acc_id = '1456875645545'
    }
    parameters {
        choice(name: 'ACCOUNT', choices: ['DEV', 'QA'], description: 'Pick ACCOUNT')
    }

    stages {
        stage('Deploy in DEV') {
            when {
                expression {
                    params.ACCOUNT == 'DEV'
                }
            }
            steps {
                echo  "Building are the project in dev account  ${env.dev_acc_id}"
            }
        }
        stage('Deploy in QA') {
            when {
                expression {
                    params.ACCOUNT == 'QA'
                }
            }
            steps {
                echo "Building are the project in qa account  ${env.qa_acc_id}"
            }
        }
    }
    post {
        always {
            deleteDir() /* clean up our workspace */
        }
    }
}