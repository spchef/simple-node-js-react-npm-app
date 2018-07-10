pipeline {
agent {
  node {
      label 'master'
      customWorkspace '/simple-node-js-react-npm-app'
  }
}
  stages {
    stage ('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage ('Deploy') {
      when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS'
              }
            }
      steps {
        sh '/simple-node-js-react-npm-app/jenkins/scripts/deliver.sh'
        input message: 'Finished using the web site? (Click "Proceed" to continue)'
        sh '/simple-node-js-react-npm-app/jenkins/scripts/kill.sh'
      }
    }
  }
}
