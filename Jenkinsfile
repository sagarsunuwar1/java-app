pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
		sh 'mvn clean package'
            }

	post { 
        success { 
            echo 'Archiving the artifacts'
	    archiveArtifacts artifacts: '**/*.war', followSymlinks: false
        }
    }
}
          stage('Build docker image') {
            steps {
                echo 'building image'
		sh 'docker build -t myregistry.local/myapp:"$BUILD_NUMBER" .'
            }
        }
            stage('Trivy scan docker image') {
            	steps {
                  echo 'scanning image'
		  sh 'trivy image myregistry.local/myapp:"$BUILD_NUMBER"'
            }
        }
	     stage('Upload image to docker registry') {
                steps {
                  echo 'Uploading image'
            }
        }
	     stage('Deploy to staging env') {
                steps {
                  echo 'staging env'
                  sh '''
		  docker stop myapp-staging || true
		  docker rm myapp-staging   || true 
		  docker run -d --name myapp-staging -p 9090:8080 myregistry.local/myapp:"$BUILD_NUMBER"
		  '''
            }
        }
    }
}

