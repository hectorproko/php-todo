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
        git branch: "${env.BRANCH_NAME}", url: 'https://github.com/hectorproko/php-todo.git'
      }
    }

    stage('Docker Image Build') {
      steps {
       // sh "docker build -t hectorproko/php-todo:${BRANCH_NAME}-${BUILD_NUMBER} ."
        sh "docker build -t hectorproko/php-todo:${env.BRANCH_NAME}-${env.BUILD_NUMBER} ."
        //echo "The branch ${env.BRANCH_NAME}"
      }
    }

    stage('Code Analysis') {
      steps {
        echo "Code Analysis"
      }
    }
  }
}
