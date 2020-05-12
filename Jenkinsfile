pipeline {
    agent any
    
    environment {
         BRANCH_NAME_NORMALIZED = "${BRANCH_NAME.toLowerCase().replace("/", "_")}"
         NODE_ENV = 'development'

           }
    
    stages {
       stage ('NPM build') {
            steps {
                script {
                    if (BRANCH_NAME ==~ /test/) {
                        withEnv(["NODE_ENV=PRODUCTION"]) {
                            sh "echo ${NODE_ENV}"
                        }
                        

                        }
                    }
                    sh "echo ${NODE_ENV}"
                }
            }
    }
}
