pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        //writeFile(file: 'test.txt', text: 'test-tset')
		bat 'npm install yarn'
		bat 'yarn --version'
      }
    }

  }
}