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
                nexusArtifactUploader artifacts: [[artifactId: 'myDevopslab', classifier: '', file: 'target/myDevopslab-0.0.12-Snapshot.war', type: 'war']], credentialsId: 'd373a20b-60f6-4028-a6f5-50234e315a04', groupId: 'com.myDevopslab', nexusUrl: '18.119.12.200:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'MyDevopsLab-SNAPSHOT', version: '0.0.12-Snapshot'
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

