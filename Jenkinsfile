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
          stage('Unittest') {
            steps {
                echo 'Running unittest'
            }
        }
            stage('Createdockerimage') {
            	steps {
                  echo 'creaing docker image'
            }
        }
    }
}

