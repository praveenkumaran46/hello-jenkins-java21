
pipeline {
  agent {
    docker {
      image 'maven:3.9-eclipse-temurin-21'
      // Run as root; set HOME so Maven uses /root/.m2; mount Jenkins cache there
      args  '-u 0:0 -e HOME=/root -v /var/lib/jenkins/.m2:/root/.m2'
    }
  }
  options { timestamps() }
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

