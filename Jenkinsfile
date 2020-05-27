
pipeline {
    agent any
    
    environment {
         
//JSON_NAME = sh(returnStdout: true, script: "sed -n '2 p' package.json | awk '{print \$2}' | sed 's/\\,//g'").trim()
//JSON_NAME = sh(returnStdout: true, script: "sed -n '2 p' package.json | awk '{print \$2}' | awk -F '/' '{print \$2}' | sed 's/\\,//g'").trim()          
//JSON_NAME = sh(returnStdout: true, script: "awk -F '/' '{print \$2}' test").trim()          
  
    }
    stages {
        stage ('Prapare value for the variable') {
            steps {
              sh "sed -n '2 p' package.json | awk '{print \$2}' | sed 's/\\,//g' > new"
            }
        }
        
        stage ('Update Italy.json') {
         when {expression { fileExists('italy.json')}}
         steps {
            sh "echo done"       
 //sh "jq --arg newname "$(sed -n '2 p' package.json | awk '{print \$2}' | sed 's/\\,//g')" '.name = $newname' italy.json > new-italy.json"
 //sh "cat new-italy.json"
            
         
           }
        }
    }
}
