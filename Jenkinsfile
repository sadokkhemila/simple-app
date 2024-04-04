pipeline {
    agent any
    tools {
        maven "maven"
    }
    stages{
        stage ("build"){
            steps{
                sh script: 'mvn clean install '
            }
        }
        
        stage('upload war to nexus'){
            steps{
                nexusArtifactUploader artifacts: [

                    [
                        artifactId: 'simple-app',
                        classifier: '',
                        file: 'target/simple-app-1.0.0.war',
                        type: 'war'
                    ]
                ],
                credentialsId: 'nexus-cred',
                groupId: 'in.javahome', 
                nexusUrl: '51.38.50.55:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'http://51.38.50.55:8081/repository/testmaven/', 
                version: '1.0.0'
            }
        }
    }
}
