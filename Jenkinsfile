pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/amruta1728/my-cicd-project.git'
            }
        }

        stage('Run Ansible') {
            // retry the whole stage automatically if it fails mid-run
            options {
                retry(2)   // you can adjust the count
            }
            steps {
                ansiblePlaybook(
                    playbook: 'ansible/deploy.yaml',
                    inventory: 'inventory'
                )
            }
        }
    }
}

