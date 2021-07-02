pipeline{
    //Directives
    agent any
   tools {
       maven 'Maven'
   }

   environment {
       ArtifactID = readMavenPom().getArtifactId()
       Version = readMavenPom().getVersion()
       GroupId = readMavenPom().getGroupID()
   }
       


    stages {
        // Specify various stage with in stages

        // stage 1: Build
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
                nexusArtifactUploader artifacts: [[artifactId: 'MyDevOpsLab', classifier: '', file: 'target\\MyDevOpsLab-0.0.2-SNAPSHOT.war', type: 'war']], 
                credentialsId: '7a382a26-044b-4866-bb1b-b4dfa4b12c61', 
                groupId: 'com.MyDevOpsLab', 
                nexusUrl: '172.16.10.28:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'MyDevOpsLab-SNAPSHOT', 
                version: '0.0.2-SNAPSHOT'
            }
        }

        // Stage4 : Print Information
        stage ('Print Environment Variables'){
            steps {
                echo "ArtifactID is '${ArtifactID}'"
                echo "Version is '${Version}'"
                echo "GroupID is '${GroupId}'"
                
                }

            }
        }

        // Stage5 : Deploy
        stage ('Deploy'){
            steps {
                echo ' Deploying is process.............'
                
                }

            }
        }

}