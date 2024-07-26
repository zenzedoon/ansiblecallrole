// Jenkinsfile
pipeline {
    agent {
        docker {
            image 'willhallonline/ansible:latest'
            args '-v /etc/ansible:/etc/ansible'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Install Ansible Roles') {
            steps {
                script {
                    sh 'ansible-galaxy install -r requirements.yml --roles-path ./roles'
                }
            }
        }
        stage('Run Ansible Playbook') {
            steps {
                script {
                    sh 'ansible-playbook -i inventory playbook.yml'
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
