pipeline {
    // add your slave label name
    agent { label 'label'}
    tools{
        maven 'maven-test'
    }
    stages {
        stage ('Checkout_SCM') {

            steps {
          	    
	     checkout scm
            }
        }

        stage ('Maven_Build') {

            steps {
               sh 'mvn clean package'
            }
        }
        
        stage ('Deploy_Tomcat') {

            steps {
	      sshagent(['label']) {
              sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war  ec2-user@13.203.226.58:/opt/tomcat11/webapps"
	      }
         }
        }
        
    }
}
