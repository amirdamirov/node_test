
pipeline {
    agent any
    
   environment {
         
JSON_NAME = sh(returnStdout: true, script: "sed -n '2 p' package.json | awk '{print \$2}' | sed 's/\\,//g' | sed 's/\"//g' | awk -F '/' '{print \$2}'").trim()
       
    }
    stages {
        stage ('Update Italy.json') {
         when {expression { fileExists('italy.json')}}
         steps {
             sh "echo ${JSON_NAME}"     
             sh "jq --arg newname "${JSON_NAME}" '.name = $newname' italy.json > new-italy.json"
             sh "cat new-italy.json"
            
         
           }
        }
    }
}
