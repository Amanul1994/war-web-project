pipeline {
   agent any
   environment {
      PATH = "/opt/maven/bin:$PATH"
   }
   
   stages {

     stage("build") {
       steps {
         sh 'mvn clean deploy'
       }
     }
     stage('sonarQuabe analysis') {
        environment {
            scannerHome = tool 'Sonar_Tools'
        }
        
        steps {
          withSonarQubeEnv('SonarQuibe') {
             
              sh "${scannerHome}/bin/sonar-scanner"

          }
        }
     }
   }
} 
