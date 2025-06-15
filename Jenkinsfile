pipeline {
  agent { label 'w1' }

  tools {
    jdk 'java17'
    maven 'maven3'
  }

  stages {
    stage('Compile') {
      when {
        changeset "gopi.txt"
      }
      steps {
        sh 'mvn compile'
      }
    }

    stage('Test') {
      when {
        changeset "gopi.txt"
      }
      steps {
        sh 'mvn test'
      }
    }

    stage('Package') {
      when {
        changeset "gopi.txt"
      }
      steps {
        sh 'mvn package'
      }
    }
  }
}
