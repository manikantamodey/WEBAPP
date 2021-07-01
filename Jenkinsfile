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
                echo ' Testing done......'

            }
        }

        //Stage3 : Publish to Repository
        stage ('Publish to Repository') {
            steps{
                nexusArtifactUploader credentialsId: 'd373a20b-60f6-4028-a6f5-50234e315a04', groupId: 'com.myDevopslab', nexusUrl: '172.16.10.234:8081', nexusVersion: 'nexus2', protocol: 'http', repository: 'MyLab-SNAPSHOT', version: '0.0.12-Snapshot'
            }
        }

        // Stage3 : Deploy
        stage ('Deploy'){
            steps {
                echo ' Deploying is process.............'
                
                }

            }
        }

        
        
}

