pipeline {
  agent any
    
   environment {
         
JSON_NAME = sh(returnStdout: true, script: "echo '${JOB_NAME}' | awk -F '/' {'print $2'}").trim()
       
    }
    stages {
        stage ('Echo') {
            steps {
              sh "echo ${JOB_NAME}"
            }
        }
    }
}
