
pipeline {
    agent any
    
    environment {
         
JSON_NAME = sh(returnStdout: true, script: "sed -n '2 p' package.json | awk '{print \$2}' | sed 's/\,//g'").trim()

           }
    
    stages {
      stage ('Update Italy.json') {
         when {expression { fileExists('italy.json')}}
         steps {
           sh "echo ${JSON_NAME}"       
 //sh "jq --arg newname "$(sed -n '2 p' package.json | awk '{print $2}' | sed 's/\"//g' | sed 's/\,//g' | cut -d "/" -f2)" '.name = $newname' italy.json > new-italy.json"
            
         
           }
        }
    }
}
