pipeline {
    agent {label 'slave-1'}
    tools {
        jdk "java17"
        maven "maven3"
    }
    stages{
        stage("git_checkout"){
            steps{
                git branch: '$branch', url: 'https://github.com/adigopi49/Boardgame.git'
            }
        }
        stage("validate"){
            steps{
                sh "mvn validate"
            }
        }
        stage("compile"){
            steps{
                sh "mvn compile"
            }
        }
        stage("test"){
            steps{
                sh "mvn test"
            }
        }
        stage("build"){
            steps{
                sh "mvn package"
            }
        }
    }
}
