def suiteRunId = UUID.randomUUID().toString()
pipeline {
  agent any
  environment {
	CI = 'true'
  }
  stages {
    stage('build') {
      steps {
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
		  def branch_name = scm.branches[0].name
		  if (branch_name.contains("*/")) {
		    branch_name = branch_name.split("\\*/")[1]
          }
		  // JOB_NAME and BUILD_NUMBER are Jenkins environment variables
		  def zipFileName = String.format('%s-%s-%s-%s.zip', JOB_NAME, branch_name, BUILD_NUMBER, java.time.LocalDate.now())
		  zip zipFile: zipFileName, archive: true, dir: 'build'
        }
      }
	}
  }
  post {
    always {
      archiveArtifacts artifacts: 'test.log', fingerprint: true
    }
  }
}