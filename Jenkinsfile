pipeline {
   agent any
  
  environment {

      sonar_url = 'http://3.109.60.255/:9000/'
      sonar_username = 'admin'
      sonar_password = 'admin'

 }

   tools {
      // Install the Maven version configured as "M3" and add it to the path.
	  jdk 'java8'
      maven "Maven3.3.9"
	   
   }
   
   stages
   {
   stage('git clone') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/GitDevops6/PractiseRepo.git'
        }
        
        }
	stage ('Compile and Build') {
         steps {
           sh '''
           mvn clean install -U  -Dmaven.test.skip=true 
           '''
                
      }
	
	}
  }
 }
