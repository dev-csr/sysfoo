pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'compile maven app'
        sh 'mvn compile'
      }
    }

    stage('test') {
      parallel {
        stage('unit test') {
          steps {
            echo 'test maven app'
            sh 'mvn clean test'
          }
        }

        stage('SCA') {
          steps {
            echo 'Software Component Analysis'
            sleep 5
          }
        }

        stage('SAST') {
          steps {
            sleep 9
          }
        }

      }
    }

    stage('package') {
      steps {
        echo 'package maven app'
        sh 'mvn package -DskipTests'
      }
    }

    stage('Container image') {
      steps {
        sleep 5
      }
    }

  }
  tools {
    maven 'maven 3.6.3'
  }
}