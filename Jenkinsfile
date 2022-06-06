pipeline {
    agent any

    tools 
	{
        
        maven "M2_HOME"
    }

    stages {
        		
		stage('SonarQube analysis') 
		  {
             steps
			   {
                   withSonarQubeEnv('sonarqube') 
				   { 
                      sh "mvn sonar:sonar"
                   }
               }
          }
	  
	  stage("Quality Gate") {
      steps {
        timeout(time: 2, unit: 'MINUTES') {
          waitForQualityGate abortPipeline: true
        }
      }
    }
        
     
     }
}
