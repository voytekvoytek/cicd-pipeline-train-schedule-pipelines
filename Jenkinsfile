DOCKER_IMAGE_NAME = "zien010101/train-schedule"
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
    stage('DeployToProduction') {
            when {
                branch 'master'
            }
            steps {
                input 'Deploy to Production?'
                milestone(1)
                kubernetesDeploy(
                    kubeconfigId: 'kubeconfig',
                    configs: 'train-schedule-kube.yml',
                    enableConfigSubstitution: true
                )
            }
        }
    }
}
  }
}
