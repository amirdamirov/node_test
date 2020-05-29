pipeline {
  agent any
    
   environment {
         
JSON_NAME = sh(returnStdout: true, script: "sed -n '2 p' package.json | awk '{print \$2}' | sed 's/\\,//g' | sed 's/\"//g' | awk -F '/' '{print \$2}'").trim()
       
    }
    stages {
        stage ('Echo') {
            steps {
              sh "echo ${JOB_NAME}"
            }
        }
    }
}
