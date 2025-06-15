pipeline {
  agent { label 'w1' }

  parameters {
    choice(name: 'RUN_STAGE', choices: ['all', 'compile'], description: 'Which stage to run')
  }

  tools {
    jdk 'java17'
    maven 'maven3'
  }

  stages {
    stage('Git Checkout') {
      when { expression { params.RUN_STAGE == 'all' } }
      steps {
        git branch: 'main', url: 'https://github.com/adigopi49/Boardgame.git'
      }
    }

    stage('Compile') {
      when { expression { params.RUN_STAGE == 'compile' || params.RUN_STAGE == 'all' } }
      steps {
        sh 'mvn compile'
      }
    }

    stage('Test') {
      when { expression { params.RUN_STAGE == 'all' } }
      steps {
        sh 'mvn test'
      }
    }

    stage('Package') {
      when { expression { params.RUN_STAGE == 'all' } }
      steps {
        sh 'mvn package'
      }
    }
  }
}
