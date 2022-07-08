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

    stage('Execute Unit Tests') {
      steps {
        echo "Execute Unit Tests"
      }
    }

    stage('Code Analysis') {
      steps {
        echo "Code Analysis"
      }
    }
  }
}
