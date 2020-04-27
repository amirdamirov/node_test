pipeline {
    agent any
    
    environment {
         PROJECT_ID = "varovskoy"
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
                withCredentials([file(credentialsId: 'gcp', variable: 'GC_KEY')]) {
                  sh("gcloud auth activate-service-account --key-file=${GC_KEY}") }
                  sh 'gcloud auth configure-docker' 
                  sh 'docker push $IMAGE:${BRANCH_NAME_NORMALIZED}'
            }
        }
      
        stage('Deploy service to K8S') {
            steps {
                  withDockerContainer(image: "gcr.io/google.com/cloudsdktool/cloud-sdk", toolName: 'latest'){
                    withCredentials([file(credentialsId: 'gcp', variable: 'GC_KEY')]) {
                      sh("HOME=$WORKSPACE gcloud --quiet auth activate-service-account --key-file=${GC_KEY}")
                      sh("HOME=$WORKSPACE gcloud container clusters get-credentials cluster-1 --zone us-central1-c --project ${PROJECT_ID}")
                      sh("HOME=$WORKSPACE kubectl apply -f deploy.yml")
                      sh("HOME=$WORKSPACE kubectl apply -f srv.yml")
                      sh("HOME=$WORKSPACE kubectl get deploy")
                      
                    
                   }
                }
            }
        } 
    }
}
