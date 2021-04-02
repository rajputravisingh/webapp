pipeline {
    agent any
    tools
    {
    maven 'maven3'
    }
  
    stages{
      stage ('Initialize'){
        steps{
          sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
             '''   
        }
      }
      
      stage ('Build'){
        steps {
          sh 'mvn clean package'
          
        }
       }
        
        stage ('Deploy-to-Tomcat'){
        steps {
            sshagent(['tomat']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war root@10.182.0.2:/var/lib/tomcat8/webapps/webapp.war'
        }
        }
      }
    
  }
}
