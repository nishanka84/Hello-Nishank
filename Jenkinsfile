def gv
String dockername = ""

pipeline {
    agent any
	environment {
		VERSION_NUMBER = '1.5.4'
		gitbranch = 'release-15.0.0'
		
	}	
	

	parameters {
		choice(name: 'Version', choices: ['1', '2', '3'], description: 'This is a test of choice')
                booleanParam(defaultValue: true, description: 'Select this option to trigger a release build', name: 'Test')
		booleanParam(defaultValue: true, description: '', name: 'Git')
        }

 stages {
      stage('Initialize') {
	  steps {
	      script {
			
		 //     def pipeline = pipelineConfig("test.yaml")
		        gv = load "variables.groovy"	   
			   
               }
	   }
       }
		   
		      
      stage('checkout') {
           steps {
		script {
		   If (params.Git == true) {
             
                       git branch: 'master', url: 'https://github.com/nishanka84/HelloTesting-World.git'
		   } else {
		       echo " Git branch not specified"
	         }
	        }      
          }
        }
  stage('Execute Maven') {
      		   when {
			   expression {
				   params.Test == true
			   }
		   }
	  steps {
		  script {
			  gv.mavenbuild()
		  }
          }
    }

       stage('Docker Build and Tag') {
           steps {
		script {
              
		   sh "docker build -t helloworld:latest ." 
		   sh "docker tag helloworld nishank/helloworld:latest"
                //sh 'docker tag samplewebapp nikhilnidhi/samplewebapp:$BUILD_NUMBER'
		   echo "Version Test ${params.Version}"
                }
          }
        }
       stage('Run Docker container on Jenkins Agent') {
             
            steps 
			{
		sh "docker stop modest_thompson "
                sh "docker run -d -p 80:8080 nishank/helloworld"
 
            }
        }
    }
}
