// Jenkins Scripted Pipeline
node {
    // You can specify a label if you want a specific agent:
    // node('my-agent-label') {

    stage('Clone Repo') {
        // Checkout repository (using Git tool configured in Jenkins)
        git url: 'https://github.com/jorgeccs/my-cicd-project.git', branch: 'master'
        // If Jenkins warns about git installation, specify the tool explicitly:
        // git tool: 'Default', url: 'https://github.com/amruta1728/my-cicd-project.git', branch: 'master'
    }

    stage('Run Ansible') {
        // Retry the ansiblePlaybook step if it fails due to restart or transient issues
        retry(2) {    // you can increase to 3 or more if needed
            ansiblePlaybook(
                playbook: 'ansible/deploy.yaml',
                inventory: 'inventory'
                credentialsId: 'my-ssh-key'
            )
        }
    }
}
