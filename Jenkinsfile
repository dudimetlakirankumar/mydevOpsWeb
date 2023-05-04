pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
                deploy adapters: [tomcat9(credentialsId: '97eeaa4d-c4e2-49be-bfae-863593a0f1d1', path: '', url: 'http://54.152.51.58:9090/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
