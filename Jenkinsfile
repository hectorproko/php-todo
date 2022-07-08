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
    
    stage('Checkout SCM') {
      steps {
        git branch: "${env.BRANCH_NAME}", url: "https://github.com/hectorproko/php-todo.git"
      }
    }

    stage('Docker Image Build') {
      steps {
        sh "docker build -t hectorproko/php-todo:${env.BRANCH_NAME}-${env.BUILD_NUMBER} ."
      }
    }
      
    stage('Start Container') {
      steps {
	sh "docker stop php-todo && docker rm php-todo" //so we can run job multiple times if we want
	sh "docker run -d --name php-todo --network tooling_app_network -p 8085:8000 hectorproko/php-todo:${env.BRANCH_NAME}-${env.BUILD_NUMBER}"
      }
    }
      
    stage('Push Image') {
      steps {
	sh "echo ${env.username}"
	sh "echo ${env.password}"
      }
    }
  }
}
