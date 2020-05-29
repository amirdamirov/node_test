pipeline {
  agent any
    
   environment {
         
  JSON_NAME = sh(returnStdout: true, script: "echo '${JOB_NAME}' | awk -F '/' {'print \$2'}").trim()
  PIPO = "salam"     
    }
    stages {
        stage ('Echo') {
            steps {
              sh "echo ${JSON_NAME}"
            }
        }
    }
}
