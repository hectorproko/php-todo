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
        git branch: 'main', url: 'https://github.com/hectorproko/php-todo.git'
      }
    }

    stage('Docker Image Build') {
      steps {
        // sh "docker build -t hectorproko/php-todo:${env.BRANCH_NAME}-${env.BUILD_NUMBER} ."
        sh "docker build -t hectorproko/php-todo:TEST-${BUILD_NUMBER} ."
      }
    }

    stage('Code Analysis') {
      steps {
        echo "Code Analysis"
      }
    }
  }
}
