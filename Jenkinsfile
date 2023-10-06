pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'compile maven app'
        sh 'mvn compile'
      }
    }

    stage('Unit test') {
      parallel {
        stage('test') {
          steps {
            echo 'test maven app'
            sh 'mvn clean test'
          }
        }

        stage('SCA') {
          steps {
            echo 'Software Component Analysis'
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

  }
  tools {
    maven 'maven 3.6.3'
  }
}