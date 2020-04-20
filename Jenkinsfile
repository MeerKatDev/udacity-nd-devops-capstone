pipeline {
  agent any
  stages {
    stage('Build Image') {
      steps {
        sh 'docker build --tag=hello .'
      }
    }

    stage("Lint Image") {
      steps {
        sh 'hadolint Dockerfile'
      }
    }

    stage('Push Image') {
      steps {
        sh './scripts/upload_docker.sh'
      }
    }
  }
}
