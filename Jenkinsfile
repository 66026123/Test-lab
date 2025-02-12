pipeline {
    agent any

    stages {
        stage("Copy file to Docker server") {
            steps {
                // Edit team33-neogym to be the same name as the pipeline job/item created in Jenkins.
                sh "scp -r /var/lib/jenkins/workspace/66026123/* root@43.208.146.8:~/66026123"
            }
        }

        stage("Build Docker Image") {
            steps {
                // Path to Ansible playbook for building the Docker image
                ansiblePlaybook playbook: "/var/lib/jenkins/workspace/66026123/playbooks/build.yaml"
            }
        }

        stage("Create Docker Container") {
            steps {
                // Path to Ansible playbook for deploying the Docker container
                ansiblePlaybook playbook: "/var/lib/jenkins/workspace/66026123/playbooks/deploy.yaml"
            }
        }
    }
}

