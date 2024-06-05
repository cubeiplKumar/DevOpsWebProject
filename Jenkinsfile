pipeline{
    agent any
    stages{
        stage('Build Package'){
            steps{
                sh "mvn clean package"
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts Artifacts: '**/target/*/war'
                }
            }
        }
        stage('Deploy Artifacts into Tomcat Server'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat_creds', path: '', url: 'http://34.207.196.182:8282')], contextPath: null, war: '**/*.war'
            }
        }
    }
}