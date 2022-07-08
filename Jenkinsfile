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
        git branch: 'docker_job', url: 'https://github.com/hectorproko/php-todo.git'
      }
    }

    stage('Docker Image Build') {
      steps {
       // sh "docker build -t hectorproko/php-todo:${BRANCH_NAME}-${BUILD_NUMBER} ."
        sh "docker build -t hectorproko/php-todo:docker_job-${BUILD_NUMBER} ."
      }
    }

    stage('Code Analysis') {
      steps {
        echo "Code Analysis"
      }
    }
  }
}
