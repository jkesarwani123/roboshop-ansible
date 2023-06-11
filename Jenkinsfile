pipeline {

    agent {
        node {
         label 'workspace'
        }
    }
    parameters {
        choice(name: 'env', choices: ['dev', 'prod'], description: 'Environment')
        string(name: 'component', defaultValue: '', description: 'component name')
    }
    stages {
        stage('Ansible') {
            steps{
                sh 'ansible-playbook -i ${component}-${env}.jkdevops.online, roboshop.yml -e ansible_user=centos -e ansible_password=DevOps321 -e env=${env} -e role_name=${component}'
            }
        }

    }
    post {
        always {
            cleanWs()
        }
    }
}