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
	    bat 'yarn test --watchAll=false --coverage=true > test.log'
      }
	}
	stage('deliver') {
      steps {
	    script {
          //DATE_TAG = java.time.LocalDate.now()
          //DATETIME_TAG = java.time.LocalDateTime.now()
		  //echo "${DATETIME_TAG}"
		  //def dt = DATE_TAG
		  //echo dt.toString()
		  //echo BUILD_TAG
		  def zipFileName = JOB_NAME + '-main-' + BUILD_NUMBER + '-' + java.time.LocalDate.now() + '.zip'
		  zip zipFile: zipFileName, archive: true, dir: 'build'
        }
		//echo dt.toString()
		//bat 'echo ${DATETIME_TAG}'
        //archiveArtifacts artifacts: 'build/*.*', fingerprint: true
		//zip zipFile: 'ui.zip', archive: true, dir: 'build', overwrite: true
      }
	}
  }
  post {
    always {
      archiveArtifacts artifacts: 'test.log', fingerprint: true
    }
  }
}