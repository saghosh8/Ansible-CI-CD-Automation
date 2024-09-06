// This is the CI/CD pipeline configuration for Jenkins. 
// The pipeline will trigger Ansible playbooks for deploying and rolling back applications.


pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/yourusername/ansible-ci-cd-pipeline.git'
            }
        }
        stage('Setup Environment') {
            steps {
                ansiblePlaybook credentialsId: 'ansible-vault', playbook: 'playbooks/setup.yml', inventory: 'inventory/staging'
            }
        }
        stage('Deploy Application') {
            steps {
                ansiblePlaybook credentialsId: 'ansible-vault', playbook: 'playbooks/deploy.yml', inventory: 'inventory/production'
            }
        }
        stage('Run Tests') {
            steps {
                sh './run-tests.sh'
            }
        }
        stage('Rolling Update') {
            steps {
                ansiblePlaybook credentialsId: 'ansible-vault', playbook: 'playbooks/update.yml', inventory: 'inventory/production'
            }
        }
    }
    post {
        failure {
            ansiblePlaybook credentialsId: 'ansible-vault', playbook: 'playbooks/rollback.yml', inventory: 'inventory/production'
        }
    }
}
