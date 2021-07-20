pipeline{
    //Directives
    agent any
    tools {
        maven 'Maven'
    }

    environment {
        GroupId = readMavenPom().getGroupId()
        ArtifactId = readMavenPom().getArtifactId()
        Version = readMavenPom().getVersion()
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
                echo ' Testing***********.'

            }
        }

        //Stage3 : Publish to Repository
        stage ('Publish to Repository') {
            steps {
                script {
                    def NexusRepo = Version.endsWith("SNAPSHOT") ? "MyDevOpsLab-SNAPSHOT" : "MyDevOpsLab-RELEASE"
                    nexusArtifactUploader artifacts: [[artifactId: 'MyDevOpsLab', classifier: '', file: "target\\${ArtifactId}-${Version}.war", type: 'war']], 
                    credentialsId: '66899253-2f04-4554-9768-1d7b49d0e9d3', 
                    groupId: "${GroupId}", 
                    nexusUrl: '172.16.10.84:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: "${NexusRepo}", 
                    version: "${Version}"


                }
                
            }
        }

        // Stage4 : Deploy
        stage ('Deploy'){
            steps {
                echo 'This is a Fresh start'
                sshPublisher(publishers: 
                [sshPublisherDesc(
                    configName: 'Ansible_controller', 
                    transfers:[
                        sshTransfer(
                            cleanRemote: false, 
                            excludes: '', 
                            execCommand: 'ansible-playbook /opt/playbooks/downloadanddeploy.yml -i /opt/playbooks/hosts', 
                            execTimeout: 120000, 
                            flatten: false, 
                            makeEmptyDirs: false, 
                            noDefaultExcludes: false, 
                            patternSeparator: '[, ]+', 
                            remoteDirectory: '', 
                            remoteDirectorySDF: false, 
                            removePrefix: '', 
                            sourceFiles: ''
                            )
                            ], 
                    usePromotionTimestamp: false, 
                    useWorkspaceInPromotion: false, 
                    verbose: false)])
            }

        }
    }

        
        
}