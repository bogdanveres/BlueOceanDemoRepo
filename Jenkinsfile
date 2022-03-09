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
            sh '''echo "execute shell 1"



'''
            sh '''sleep 10
'''
          }
        }

        stage('ExecuteShell 2') {
          steps {
            sh 'echo "execute shell 2"'
            sh 'sleep 10'
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