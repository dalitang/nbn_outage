pipeline {
  agent any
  stages {
    stage('s1') {
      parallel {
        stage('j1') {
          steps {
            build(job: 'j1m', wait: true)
          }
        }
        stage('j2') {
          steps {
            build(job: 'j10s', wait: true)
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