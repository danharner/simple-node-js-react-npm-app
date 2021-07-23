pipeline {
  agent any
      environment {
        CI = 'true'
    }

    stage('build') {
      steps {
        //writeFile(file: 'test.txt', text: 'test-tset')
		//bat 'path'
		bat 'yarn install'
		bat 'yarn build'
      }
    }

	stage('Test') {
      steps {
	    bat 'yarn test --watchAll=false'
      }
	}

  }
}