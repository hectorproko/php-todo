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
    // This is already done in the job
    //stage('Checkout SCM') {
    //  steps {
    //    git branch: 'main', url: 'https://github.com/hectorproko/php-todo.git'
    //  }
    //}

    stage('Docker Image Build') {
      steps {
       // sh "docker build -t hectorproko/php-todo:${BRANCH_NAME}-${BUILD_NUMBER} ."
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
