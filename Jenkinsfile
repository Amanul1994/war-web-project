pipeline {
   agent any
   environment {
      PATH = "/opt/maven/bin:$PATH"
   }
   
   stages {

     stage("build") {
       steps {
         echo ".......build started ......."
         sh 'mvn clean package -Dmaven.test.skip=true'
         echo ".......build completed........"
       }
     }
     stage("test") {
       steps {
         echo ".......unit test  started ......."
         sh 'mvn surefire-report:report'
         echo ".......unit test completed........"
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
