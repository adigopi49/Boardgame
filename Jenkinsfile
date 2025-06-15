pipeline {
  agent { label 'w1' }

  tools {
    jdk 'java17'
    maven 'maven3'
  }

  stages {
    stage('Git Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/adigopi49/Boardgame.git'
      }
    }

    stage('Compile') {
      steps {
        sh 'mvn compile'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }
  } // 👈 this closes "stages"

} // 👈 this closes "pipeline"
