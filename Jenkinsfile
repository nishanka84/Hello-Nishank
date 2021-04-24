
@Library('shared-nishank') _


pipeline {
    agent none
    stages {
        stage ('Example') {
            steps { 
                testing name: 'git'
            }
        }
         stage ('Email') {
             steps {  
                sources type: "slack", message: "a slack notification"
             }
         }    
    }
}
