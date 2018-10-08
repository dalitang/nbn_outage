pipeline {
  agent any
  stages {
    stage('s1') {
      parallel {
        stage('j1') {
          steps {
            echo '1'
            build 'j1m'
          }
        }
        stage('j2') {
          steps {
            echo '2'
            build 'j10s'
          }
        }
      }
    }
    stage('s2') {
      parallel {
        stage('j1') {
          steps {
            build 'j10s'
          }
        }
        stage('j2') {
          steps {
            build 'j1m'
          }
        }
      }
    }
  }
}