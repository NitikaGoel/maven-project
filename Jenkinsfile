pipeline {
  agent  any
  tools {
	maven 'localmaven'
  }
  stages {
    stage('Initialize') {
      steps{
        bat 'mvn clean package'
      }
	  post{
		success {
			echo 'Build successfull'
			archiveArtifacts artifacts : '**/target/*.war'
		}
	  }
    }
	stage('Deploy to stage') {
		steps {
		 build job : 'deploy-build'
		}
	}
	stage('Deploy to production') {
		
		
		steps {
			timeout(time:5, unit:'DAYS') {
				input message : 'Approve production deployment'
			}
			build job : 'deploy-build-to-production'
		}
		post {
			success {
				echo 'Deployed Successfully'
			}
			failure {
				echo 'Deployment failed'
			}
		}
	}
 }
}
