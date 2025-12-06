
pipeline {
  agent {
    docker {
      image 'maven:3.9-eclipse-temurin-21'
      args  '-v $HOME/.m2:/root/.m2' // cache Maven repo to speed up builds
    }
  }
  options { timestamps(); ansiColor('xterm') }
  stages {
    stage('Checkout') {
      steps { checkout scm }
    }
    stage('Build') {
      steps {
        sh 'mvn -B -ntp clean package'
      }
    }
    stage('Archive Artifacts') {
      steps {
        archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
      }
    }
  }
}
