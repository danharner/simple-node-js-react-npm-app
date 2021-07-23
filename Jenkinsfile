pipeline {
  agent any
  environment {
	CI = 'true'
  }
  stages {
    stage('build') {
      steps {
        //writeFile(file: 'test.txt', text: 'test-tset')
	    //bat 'path'
	  bat 'yarn install'
	  bat 'yarn build'
      }
    }
	stage('test') {
      steps {
	    bat 'yarn test --watchAll=false'
      }
	}
	stage('deliver') {
      steps {
        archiveArtifacts artifacts: 'build/*.*', fingerprint: true
      }
	}
  }
}