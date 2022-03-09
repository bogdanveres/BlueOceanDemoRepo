pipeline {
  agent any
  stages {
    stage('Prepare Env') {
      steps {
        node(label: 'built-in') {
          sleep 5
        }

      }
    }

    stage('Parallel Execution') {
      parallel {
        stage('ExecuteShell 1') {
          steps {
            sh 'echo "execute shell 1"'
          }
        }

        stage('ExecuteShell 2') {
          steps {
            sh 'echo "execute shell 2"'
          }
        }

      }
    }

    stage('Clean') {
      steps {
        cleanWs()
      }
    }

  }
}