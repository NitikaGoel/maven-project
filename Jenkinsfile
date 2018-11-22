pipeline {
  agent  any
  stages {
    stage('Initialize') {
      steps{
        sh 'mvn clean package'
      }
	  post{
		success {
			echo 'Build successfull'
			archiveArtifacts artifacts : '**/target/*.war'
		}
	  }
    }
 }
}
