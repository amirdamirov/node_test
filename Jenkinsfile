pipeline {
    agent any
    
    environment {
         PROJECT_ID = "amir-265013"
         IMAGE = "gcr.io/$PROJECT_ID/node-app"
         BRANCH_NAME_NORMALIZED = "${BRANCH_NAME.toLowerCase().replace("/", "_")}"
           }
    
    stages {
        stage('Build') {
            steps {
                sh ' docker build -t ${IMAGE}:${BRANCH_NAME_NORMALIZED} . '
                
            }
        }
        stage('Push') {
            steps {
                withCredentials([file(credentialsId: 'jenkins_secret', variable: 'GC_KEY')]) {
                  sh("gcloud auth activate-service-account --key-file=${GC_KEY}") }
                  sh ' gcloud auth configure-docker  ' 
                  sh ' docker push $IMAGE:${BRANCH_NAME_NORMALIZED} '
            }
        }
      
    }
}