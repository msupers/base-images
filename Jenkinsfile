pipeline {
  agent {
    docker {
      image 'centos:7'
    }

  }
  stages {
    stage('') {
      steps {
        sh 'echo "hello 1"'
      }
    }

    stage('stage2') {
      steps {
        sleep 5
      }
    }

    stage('stage3') {
      steps {
        echo 'hello'
      }
    }

    stage('stage4') {
      steps {
        archiveArtifacts(artifacts: 'dddd', excludes: 'tar')
      }
    }

    stage('stage5') {
      steps {
        archiveArtifacts(defaultExcludes: true, artifacts: 'bae', onlyIfSuccessful: true)
      }
    }

  }
}