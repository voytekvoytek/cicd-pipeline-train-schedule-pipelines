pipeline {
  agent any
  stages {
    stage ('Build') {
      steps {
        echo "Running a build"
        sh './gradlew build --no-deamon'
        archiveArtifacts artifacts: 'dist/trainSchedule.zip
      }
    }
  }
}
