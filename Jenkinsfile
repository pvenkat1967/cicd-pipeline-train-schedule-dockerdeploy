pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
	stage('build docker image') {
	  when {
	     branch 'master'
	  }
	    steps {
	        script {
		  app = docker.build("pvenkat1967/cicd-pipeline-train-schedule-dockerdeploy")
		  app.inside {
		    sh 'echo $(curl localhost:8080)
		  }
            }
	}    
    }
     
}
