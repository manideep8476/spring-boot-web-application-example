pipeline  {
	agent any
	tools {
		maven 'Maven3'
		jdk 'JDK8'
	}

	stages {
		stage('init') {
			steps {
				sh '''
					echo "PATH = ${PATH}"
					echo "M2_HOME = ${M2_HOME}"
				'''
			}
		}


		stage ('Build') {
			steps {
				sh 'mvn install'
			}
		}
		stage 'Docker build'
    	steps {
		
	    	sh '''
			
	
		        sudo docker build -t demo
	
	        	sudo docker run demo
		    '''
	    }
 
        stage 'Docker push'
            docker.withRegistry('https://464375181876.dkr.ecr.us-east-1.amazonaws.com/manideep8476', 'ecr:us-east-1:ECR-credentials') {
            docker.image('demo').push('latest')
        }
	}
}
