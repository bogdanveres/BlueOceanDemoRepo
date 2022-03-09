pipeline {
  agent any
  stages {
    stage('Prepare Env') {
      steps {
        node(label: 'MacOS') {
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
            writeFile(file: 'pipeline_steps.log', text: 'I\'m running inside: ${WORKSPACE} ')
          }
        }

      }
    }

    stage('Clean') {
      steps {
        timestamps() {
          sh 'echo "timestamp"'
        }

        echo 'Test message ${WORKSPACE}'
        archiveArtifacts '**/*.log'
      }
    }

    stage('Delete Workspace') {
      steps {
        cleanWs()
        input(message: 'Do you want to delete workspace?', id: 'OK')
      }
    }

  }
}