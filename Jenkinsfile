pipeline {
    agent any

    environment {
        ANSIBLE_HOME = tool 'Ansible'
    }

      stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ramalaxmibandi/ansible-pipeline'
            }
        }

        stage(' Ansible initialise') {
            steps {
                script {
                    // Run Ansible playbook
                    sh 'ansible-playbook -i inventory initial.yml'
 '
                }
            }
        }
		stage('kube dependencies') {
            steps {
                script {
                    // Run Ansible playbook
                    sh 'ansible-playbook -i inventory kube-dependencies.yml'
                }
            }
        }
		stage('master') {
            steps {
                script {
                    // Run Ansible playbook
                    sh 'ansible-playbook -i inventory master.yml'
                }
            }
        }
		stage('worker') {
            steps {
                script {
                    // Run Ansible playbook
                    sh 'ansible-playbook -i inventory workers.yml'
                }
            }
        }
    }
}
