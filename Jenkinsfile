pipeline {
  agent any
  stages {
    stage('Prepare Env') {
      steps {
        node(label: 'MacOSAgent') {
          echo 'Executed on TestAgent'
          sleep 15
        }

      }
    }

    stage('Execute Shell') {
      parallel {
        stage('Run shell 1') {
          steps {
            node(label: 'built-in') {
              echo 'executed on built-in agent'
              sleep 5
              timestamps() {
                echo 'this is the line with timestamp'
              }

            }

          }
        }

        stage('Run shell 2') {
          steps {
            node(label: 'MacOSAgent') {
              echo 'executed on MacOSAGent'
              sleep 5
            }

          }
        }

      }
    }

    stage('Save results') {
      steps {
        node(label: 'MacOSAgent') {
          writeFile(file: 'test_execution.log', text: 'bla bla bla')
        }

      }
    }

    stage('Publish results') {
      steps {
        node(label: 'MacOSAgent') {
          archiveArtifacts '**/*.log'
        }

      }
    }

    stage('Clean Workspace') {
      steps {
        node(label: 'MacOSAgent') {
          cleanWs(deleteDirs: true, cleanWhenAborted: true, cleanWhenFailure: true, cleanWhenNotBuilt: true, cleanWhenSuccess: true, cleanWhenUnstable: true, cleanupMatrixParent: true)
        }

      }
    }

  }
  environment {
    JENKINS_JOB = 'BlueOcean'
  }
}