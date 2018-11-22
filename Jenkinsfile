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
 }
}
