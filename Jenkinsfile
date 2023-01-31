pipeline {
    agent any
    environment {
        //dev_acc_id = '1545788888778'
        //qa_acc_id = '1456875645545'
        my_account = "${params.ACCOUNT}"
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
                sh "echo Building are the project in dev aws account."
                getAccountNumber(env.my_account)
            }
        }
        stage('Deploy in QA') {
            when {
                expression {
                    params.ACCOUNT == 'QA'
                }
            }
            steps {
               sh "echo Building are the project in qa aws account."
               getAccountNumber(env.my_account)
            }
        }
    }
    post {
        always {
            deleteDir() /* clean up our workspace */
        }
    }
}