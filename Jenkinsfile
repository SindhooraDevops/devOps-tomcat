pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
           ## post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{

                deployment adapters: [tomcat9(credentialsID:'tomcatcred',path:'',url:'http://3.90.248.181:8080/')],contextpath:'devOps-tomcat',war:'**/*.war'
            }
        }
    }
}
