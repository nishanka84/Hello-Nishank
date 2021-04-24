
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
                notify type: "slack", message: "a slack notification"
             }
         }    
    }
}
