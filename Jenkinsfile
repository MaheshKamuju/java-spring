pipeline {
      agent any
      stages {
         stage ('Build') {
          steps {
             sh '''cd $WORKSPACE
                   docker build -t devops:v${BUILD_NUMBER} .'''
             }
           }
           stage('push ECR'){
            steps {
                sh '''aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 102058874917.dkr.ecr.us-east-2.amazonaws.com
           		    
	
					docker tag devops:v${BUILD_NUMBER} 102058874917.dkr.ecr.us-east-2.amazonaws.com/devops:v${BUILD_NUMBER}

		   docker push 102058874917.dkr.ecr.us-east-2.amazonaws.com/devops:v${BUILD_NUMBER}
       '''
          }
          }
          }
        }
