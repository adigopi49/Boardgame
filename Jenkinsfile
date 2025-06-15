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

    stage('Compile-a') {
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

    stage('build-docker') {
      steps {
        script{
          withDockerRegistry(credentialsId: 'docker-cred') {
            sh "docker build -t gopiadi/bank:v1"
          }
        }
      }
    }
  }
}
