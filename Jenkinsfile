pipeline {
      agent any
      stages {
         stage ('Build') {
          steps {
             sh '''cd $WORKSPACE
                   docker build -t devops-spring:v${BUILD_NUMBER} .'''
             }
           }
           stage('Push Image to ECR'){
            steps {
                sh '''aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 559050209565.dkr.ecr.us-east-1.amazonaws.com
           		    
			                 docker tag devops-spring:v${BUILD_NUMBER} 559050209565.dkr.ecr.us-east-1.amazonaws.com/devops-spring:v${BUILD_NUMBER}
                    	 docker push 559050209565.dkr.ecr.us-east-1.amazonaws.com/devops-spring:v${BUILD_NUMBER}
		   
       '''
            }
          }
          }
        }
