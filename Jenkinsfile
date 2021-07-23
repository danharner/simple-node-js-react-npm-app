pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        //writeFile(file: 'test.txt', text: 'test-tset')
		//bat 'path'
		bat 'yarn install'
		bat 'yarn build'
      }
    }

  }
}