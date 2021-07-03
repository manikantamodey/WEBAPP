pipeline{
    //Directives
    agent any
    tools {
        maven 'Maven'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }

        //Stage3 : Publish to Repository
        stage ('Publish to Repository') {
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'MyDevOpsLab', classifier: '', file: 'target\\MyDevOpsLab-0.0.2-SNAPSHOT.war', type: 'war']], 
                credentialsId: '6bca8a65-3bf8-4979-9e7d-fb2b45c36db4', 
                groupId: 'com.MyDevOpsLab', 
                nexusUrl: '172.16.10.168:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'MyDevOpsLab-SNAPSHOT', 
                version: '0.0.2-SNAPSHOT'
            }
        }

        // Stage4 : Deploy
        stage ('Deploy'){
            steps {
                echo 'This is a Fresh start'
            }

        }
    }

        
        
}