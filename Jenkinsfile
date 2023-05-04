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
                deploy adapters: [tomcat9(credentialsId: '4f17b9a9-ed38-4d7b-b188-da2100abec03', path: '', url: 'http://54.152.51.58:9090/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
