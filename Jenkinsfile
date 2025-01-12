pipeline {
   agent any
   environment {
      PATH = "/opt/maven/bin:$PATH"
   }
   
   stages {

     stage("build") {
       steps {
         sh 'mvn clean package'
       }
     }
     stage('sonarQuabe analysis') {
        environment {
            scannerHome = tool 'sonar_tools'
        }
        
        steps {
          withSonarQubeEnv('sonar_server') {
             
              sh "${scannerHome}/bin/sonar-scanner"

          }
        }
     }
   }
} 
