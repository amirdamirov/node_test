pipeline {
    agent any
    
    environment {
         BRANCH_NAME_NORMALIZED = "${BRANCH_NAME.toLowerCase().replace("/", "_")}"
           }
    
    stages {
        stage('Build') {
            steps {
                sh 'echo ${BRANCH_NAME}'
                
            }
        }
    }
}

