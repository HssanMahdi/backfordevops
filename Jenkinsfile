pipeline {
    agent any
    environment { 

        registry = "cheumas/image3" 

        registryCredential = 'jenkins-dockerhub' 

        dockerImage = '' 

    }
//      environment {
//      DOCKERHUB_CREDENTIALS = credentials('jenkins-dockerhub')
//   }
//     environment {
//        NEXUS_VERSION = "nexus3"
//          NEXUS_PROTOCOL = "http"
//         NEXUS_URL = "192.168.1.6:8081"
//          NEXUS_REPOSITORY = "maven-central-repository"
//         NEXUS_CREDENTIAL_ID = "jenkins-nexus"
//      }
    stages {
//         stage('Git checkout') {
//         steps {
//            git branch: 'cheima', credentialsId: '708d09c8-1a8b-400e-b7eb-9336519ddcbe', url: 'https://github.com/HssanMahdi/backfordevops.git'
//           }
//       }
	  
//          stage("Maven Clean") {
//              steps {
//                 sh "mvn clean"
       
//             }
//          }
        
//         stage("Maven Compile") {
//            steps {
//                 sh "mvn compile"
//              }
//         }
		
	
      
//          stage("Maven Build") {
//              steps {
//                 script {
//                      sh "mvn package -DskipTests=true"
//                }
//              }
//         }
// 	         stage('MVN SONARQUBE') {
//              steps {
//                sh 'mvn sonar:sonar -Dsonar.login=admin -Dsonar.password=sonar'
//              }
//           }
                
//         stage("Publish to Nexus Repository Manager") {
//              steps {
//                 script {
//                      pom = readMavenPom file: "pom.xml";
//                      filesByGlob = findFiles(glob: "target/*.${pom.packaging}");
//                      echo "${filesByGlob[0].name} ${filesByGlob[0].path} ${filesByGlob[0].directory} ${filesByGlob[0].length} ${filesByGlob[0].lastModified}"
//                      artifactPath = filesByGlob[0].path;
//                     artifactExists = fileExists artifactPath;
//                     if(artifactExists) {
//                       echo "*** File: ${artifactPath}, group: ${pom.groupId}, packaging: ${pom.packaging}, version ${pom.version}";
//                         nexusArtifactUploader(
//                              nexusVersion: NEXUS_VERSION,
//                             protocol: NEXUS_PROTOCOL,
//                             nexusUrl: NEXUS_URL,
//                             groupId: pom.groupId,
//                              version: pom.version,
//                              repository: NEXUS_REPOSITORY,
//                             credentialsId: NEXUS_CREDENTIAL_ID,
//                              artifacts: [
//                                  [artifactId: pom.artifactId,
//                                  classifier: '',
//                                  file: artifactPath,
//                                  type: pom.packaging],
//                                  [artifactId: pom.artifactId,
//                                  classifier: '',
//                                  file: "pom.xml",
//                                  type: "pom"]
//                              ]
//                         );
//                      } else {
//                        error "*** File: ${artifactPath}, could not be found";
//                     }
//                 }
//             }
//         }
	 stage('Building our image') { 

            steps { 

                script { 

                    dockerImage = docker.build registry + ":$BUILD_NUMBER" 

                }

            } 

        }

       stage('Deploy our image') { 

            steps { 

                script { 

                    docker.withRegistry( '', registryCredential ) { 

                        dockerImage.push() 

                    }

                } 

            }

        } 

        
          stage('Cleanin up') { 

            steps { 

                sh "docker rmi $registry:$BUILD_NUMBER" 

            }

        } 
       
                          

		
    }
       
    
}  