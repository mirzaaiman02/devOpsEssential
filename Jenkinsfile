// MOHAMAD MIRZA AIMAN BIN ZULKIPLE

pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages{      //stages 1 and 2
        stage('Build'){                       // stage 1
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
        stage ('Deploy to tomcat server') {       // stage 2
            steps{
                deploy adapters: [tomcat7(credentialsId: '3e031361-be15-44f2-8ffd-1ad025532232', path: '', url: 'http://3.108.221.41:8282/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}