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
            stage('Createdockerimage') {
            	steps {
                  echo 'creaing docker image'
            }
        }
    }
}

