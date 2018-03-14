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
		stage ('Docker') {
	
		steps {
		
		sh '''
			
	
		visudo docker build -t boot-docker:${BUILD_NUMBER} ${WORKSPACE}
	
			visudo docker run -p 8081:8585 boot-docker:${BUILD_NUMBER}

		'''
			}
	
	}

		
	}
}
