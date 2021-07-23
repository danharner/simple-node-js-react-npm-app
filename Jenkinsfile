def suiteRunId = UUID.randomUUID().toString()
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
	    script {
          DATE_TAG = java.time.LocalDate.now()
          DATETIME_TAG = java.time.LocalDateTime.now()
		  //echo "${DATETIME_TAG}"
		  def dt = DATE_TAG
		  echo dt.toString()
		  echo BUILD_TAG
		  //zip zipFile: 'ui.zip', archive: true, dir: 'build', overwrite: true
        }
		//echo dt.toString()
		//bat 'echo ${DATETIME_TAG}'
        //archiveArtifacts artifacts: 'build/*.*', fingerprint: true
		//zip zipFile: 'ui.zip', archive: true, dir: 'build', overwrite: true
      }
	}
  }
}