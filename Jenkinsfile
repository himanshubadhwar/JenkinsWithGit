pipeline {
    agent any
    environment {
        name = 'master'  
    }
    parameters {
        string(name: 'person', defaultValue: 'Himanshu Badhwar', description: 'Who are you?')
        booleanParam(name: 'isMale', defaultValue: true, description: "")
        choice(name: 'City', choices: ['Jaipur', 'Mumbai', 'Pune'], description: "")
    }
    stages {
        stage('Run a command') {
            steps {
                sh '''
                ls
                date
                pwd
                '''
            }
        }
        stage('Environment variables') {
            environment {
                username = 'agent'  
            }
            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${name}"'
                sh 'echo "${username}"'
            }
        }
        stage('Parameters') {
            steps {
                echo 'Deploy on Test'
                sh 'echo "${name}"'
                sh 'echo "${person}"'
            }
        }
        stage('Continue') {
            input {
                message "Should we continue?"
                ok "Yes we should"
            }
            steps {
                echo 'Deploy on Prod'
            }
        }
        stage('Deploy on Prod') {
            steps {
                echo 'Deploy on Prod'
            }
        }
    }
    post {
        always { 
            echo 'I will always say Hello again!'
        }
        failure { 
            echo 'Failure!'
        }
        success { 
            echo 'Success!'
        }
    }
}
