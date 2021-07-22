pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        //writeFile(file: 'test.txt', text: 'test-tset')
		bat 'npm install -g yarn'
		bat 'yarn --version'
      }
    }

  }
}