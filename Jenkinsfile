pipeline {
   agent any
  
  environment {

      sonar_url = 'http://3.108.223.17:9000/'
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
	   stage ('Sonarqube Analysis'){
           steps {
           withSonarQubeEnv('sonarqube') {
           sh '''
           mvn clean package org.jacoco:jacoco-maven-plugin:prepare-agent install -Dmaven.test.failure.ignore=false
           mvn -e -B sonar:sonar -Dsonar.java.source=1.8 -Dsonar.host.url="${sonar_url}" -Dsonar.login="${sonar_username}" -Dsonar.password="${sonar_password}" -Dsonar.sourceEncoding=UTF-8
           '''
	   }
	   }
	   }
  }
 }
