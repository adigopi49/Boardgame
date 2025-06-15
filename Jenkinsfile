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

    stage('Build Docker Image') {
      steps {
        script {
          withDockerRegistry(credentialsId: 'docker-cred', url: 'https://index.docker.io/v1/') {
            sh 'docker build -t gopiadi/banl:v1 .'
            // Optional: push the image
            // sh 'docker push gopiadi/banl:v1'
          }
        }
      }
    }
  }
}
