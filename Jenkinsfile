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
                nexusArtifactUploader artifacts: [[artifactId: 'myDevopslab', classifier: '', file: 'target/myDevopslab-0.0.2-Snapshot.war', type: 'war']], credentialsId: '1531c45c-f79d-4e60-b219-2c529930adfe', groupId: 'com.myDevopslab', nexusUrl: '172.16.10.242:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'MyDevopsLab-SNAPSHOT', version: '0.0.2-Snapshot'
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

