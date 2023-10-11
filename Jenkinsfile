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
                credentialsId: 'nexus-connex',
                groupId: 'in.javahome', 
                nexusUrl: '3.88.191.212:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'http://3.88.191.212:8081/repository/test-maven', 
                version: '1.0.0'
            }
        }
    }
}