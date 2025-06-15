pipeline {
  agent { label 'w1' }

  tools {
    jdk 'java17'
    maven 'maven3'
  }

  parameters {
    choice(
      name: 'RUN_STAGE',
      choices: ['compile', 'test', 'package'],
      description: 'Select which stage to execute'
    )
  }

  stages {
    stage('Compile') {
      when {
        expression { params.RUN_STAGE == 'compile' }
      }
      steps {
        sh 'mvn compile'
      }
    }

    stage('Test') {
      when {
        expression { params.RUN_STAGE == 'test' }
      }
      steps {
        sh 'mvn test'
      }
    }

    stage('Package') {
      when {
        expression { params.RUN_STAGE == 'package' }
      }
      steps {
        sh 'mvn package'
      }
    }
  }
}
