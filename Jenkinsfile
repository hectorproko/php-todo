pipeline {
    agent any

    stages {
        stage("Initial cleanup") {
            steps {
                dir("${WORKSPACE}") {
                deleteDir()
                }
            }
        }
        
        stage('SCM Checkout') {
            steps {
                git branch: 'HisJenkinsfile', url: 'https://github.com/hectorproko/ansible-config-mgt.git'
            }
        }
        stage('Prepare Ansible For Execution') {
            steps {
                sh 'echo ${WORKSPACE}' 
                sh 'sed -i "3 a roles_path=${WORKSPACE}/roles" ${WORKSPACE}/deploy/ansible.cfg'  
                sh 'export ANSIBLE_CONFIG=${WORKSPACE}/deploy/ansible.cfg'
            }
        }
        stage('Execute Ansible') {
            steps {
                ansiblePlaybook credentialsId: 'private-key', installation: 'Ansible', inventory: '${WORKSPACE}/inventory/${inventory}.ini', playbook: 'playbooks/site.yml'
                //ansiblePlaybook become: true, colorized: true, credentialsId: 'private-key', disableHostKeyChecking: true, installation: 'ansible', inventory: '${WORKSPACE}/inventory/${inventory}', playbook: 'playbooks/site.yml'
            }
        }
        stage ('Deploy Artifact') {
            steps {
              script {
                def server = Artifactory.server 'artifactory-server'
                def uploadSpec = """{
                  "files": [{
                     "pattern": "php-todo.zip",
                     "target": "php-todo"
                  }]
                }"""
              server.upload(uploadSpec) 
              }
            }
        }
    }
}

/* The code below will print the words Hello World
to the screen, and it is amazing */
