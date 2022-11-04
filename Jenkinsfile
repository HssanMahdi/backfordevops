pipeline { 
     agent any
  
   stages{
        
       
        stage('MVN CLEAN') { 
            steps { 
               sh' mvn clean install -DskipTests' 
                
            }
        }
		stage('SonarQube') {
			steps {
				script {
					withSonarQubeEnv('sonarQubeMahdi') {
						sh' mvn sonar:sonar'
					}
				}
			}
		}
   }
}