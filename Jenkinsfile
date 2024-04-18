// MOHAMAD MIRZA AIMAN BIN ZULKIPLE
<role rolename="manager-gui"/>
  <role rolename="admin-gui"/>
  <role rolename="manager-script"/>
  <role rolename="manager-jmx"/>
  <role rolename="manager-status"/>
Jump
<user username="admin" password="#Mirza_9854!" roles="manager-gui,admin-gui,manager-script,manager-jmx,manager-status"
pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages{      //stages 1 and 2
        stage('Build'){                       // stage 1
            steps{
                bat 'mvn clean package'
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
                deploy adapters: [tomcat7(credentialsId: '3e031361-be15-44f2-8ffd-1ad025532232', path: '', url: 'http://localhost:8181/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
