pipeline {
  agent {
    node {
      label 'nbn'
    }

  }
  stages {
    stage('Data Ingestion ') {
      parallel {
        stage('Callview (IVR)') {
          agent {
            node {
              label 'nbn_di'
            }

          }
          steps {
            echo 'nba_raw_ivr_di'
            sleep(time: 3, unit: 'MINUTES')
          }
        }
        stage('SSP Google Analytics') {
          steps {
            echo 'nbn_raw_ssp_google_analytics_di'
            sleep(unit: 'MINUTES', time: 2)
          }
        }
        stage('Diagnostic Microservices Bambi Splunk') {
          steps {
            echo 'nba_raw_bambi_splunk_di'
          }
        }
        stage('iTAM') {
          steps {
            echo 'nba_raw_itam_di'
          }
        }
        stage('NBN Topology') {
          steps {
            echo 'nba_raw_topology_di'
          }
        }
        stage('Siebel Customer Mapping') {
          steps {
            echo 'nba_raw_siebel_customer_di'
          }
        }
      }
    }
    stage('Kafka Raw') {
      steps {
        echo 'Receive Msg from data sources'
      }
    }
    stage('Data Wrangling') {
      parallel {
        stage('TAAA Stop') {
          steps {
            echo 'nbn_taaa_stop_dw'
          }
        }
        stage('SIP') {
          steps {
            echo 'sip'
          }
        }
        stage('ExtraHop') {
          steps {
            echo 'extrahop'
          }
        }
        stage('iTAM Planned Outage') {
          steps {
            echo 'itam planned outage'
          }
        }
        stage('iTAM Unplanned Outage') {
          steps {
            echo 'unplanned'
          }
        }
        stage('') {
          steps {
            echo 'unplanned'
          }
        }
      }
    }
    stage('Kafka Processed') {
      steps {
        echo 'Push back new topics'
      }
    }
  }
}