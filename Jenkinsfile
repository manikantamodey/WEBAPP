pipeline{
    //Directives
    agent any
   tools {
       maven 'Maven'
   }

   environment {
       ArtifactId = readMavenPom().getArtifactId()
       Version = readMavenPom().getVersion()
       GroupId = readMavenPom().getGroupId()
       
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
            steps {

                script{
                    def NexusRepo = Version.endsWith("SNAPSHOT") ? "MyDevOpsLab-SNAPSHOT" : "MyDevOpsLab-RELEASE"

                    nexusArtifactUploader artifacts: [[artifactId: 'MyDevOpsLab', classifier: '', file: "target/${ArtifactId}-${Version}.war", type: 'war']], 
                    credentialsId: '7a382a26-044b-4866-bb1b-b4dfa4b12c61', 
                    groupId: "${GroupId}", 
                    nexusUrl: '172.16.10.28:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: "${NexusRepo}", 
                    version: "${Version}"
                }

            }
            
        }

        // Stage4 : Print Information
        stage ('Print Environment Variables'){
            steps {
                echo "ArtifactID is '${ArtifactId}'"
                echo "Version is '${Version}'"
                
                
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