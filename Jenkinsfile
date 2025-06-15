pipeline {
  agent { label 'w1' }

  tools {
    jdk 'java17'
    maven 'maven3'
  }

  stages {
    stage('Git Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/adigopi49/practice.git'
      }
    }

    stage('Compile') {
      steps {
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('build') {
      steps {
        sh 'mvn package'
      }
    }
  }
}
