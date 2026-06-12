pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Ansible Syntax Check') {
            steps {
                sh 'ansible-playbook --syntax-check playbooks/site.yml'
            }
        }

        stage('Ansible Ping Target') {
            steps {
                sh 'ansible target -m ping'
            }
        }

        stage('Manual Approval') {
            steps {
                input message: 'Code pushed to GitHub. Do you want to run the Ansible user provisioning playbook?',
                      ok: 'Approve and Run'
            }
        }

        stage('Run User Provisioning Playbook') {
            steps {
                sh 'ansible-playbook playbooks/site.yml'
            }
        }
    }

    post {
        success {
            echo 'User provisioning completed successfully.'
        }
        failure {
            echo 'User provisioning failed.'
        }
    }
}
