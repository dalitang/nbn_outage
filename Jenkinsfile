pipeline {
  agent any
  stages {
    stage('s1') {
      parallel {
        stage('j1') {
          steps {
            echo '1'
            build (job: 'j1m', wait: false)
          }
        }
        stage('j2') {
          steps {
            echo '2'
            build (job: 'j10s', wait: false)
          }
        }
      }
    }
    stage('s2') {
      parallel {
        stage('j1') {
          steps {
            build (job: 'j10s', wait: false)
          }
        }
        stage('j2') {
          steps {
            build (job: 'j1m', wait: false)
          }
        }
      }
    }
  }
}
