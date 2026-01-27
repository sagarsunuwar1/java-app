pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
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

