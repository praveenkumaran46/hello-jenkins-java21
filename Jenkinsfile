steps {
sh 'mvn clean package'
}
}
stage('Archive') {
steps {
archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
}
}
}
}
