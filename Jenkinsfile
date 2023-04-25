pipeline {
  agent any
  stages {
    stage('Git Checkout') {
      steps {
        git url: 'https://github.com/preet0807/DevOps.git', branch: 'main'
      }
    }
    stage('Build') {
      steps {
        sh 'pip install -r requirements.txt'
        sh 'python app.py'
      }
    }
  }
}
