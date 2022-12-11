  pipeline{
    agent any
 
    stages{
       stage('Git'){
            steps{
               git 'https://github.com/chaimabenkhedher/ProjetDevOps.git'
                
            }
        }
       stage('maven compile'){
            steps{
                                bat 'c:/maven/bin/mvn clean'
                                bat 'c:/maven/bin/mvn compile'

            }
        }   
      stage('maven build'){
            steps{
                               bat 'c:/maven/bin/mvn clean'
                               bat 'c:/maven/bin/mvn package'


            }
        }   
      stage('Sonar') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        bat "c:/maven/bin/mvn sonar:sonar \
  -Dsonar.projectKey=devops \
  -Dsonar.host.url=http://192.168.33.10:9000 \
  -Dsonar.login=9b599438496c729da958e4e0a1f0191f96e09208"
   
        }
        }
       
      stage('Nexus') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        bat "c:/maven/bin/mvn clean package 
          deploy:deploy-file -DgroupId=tn.esprit 
          -DartifactId=ExamThourayaS2 
          -Dversion=0.0.1-SNAPSHOT 
          -DgeneratePom=true -Dpackaging=jar 
          -DrepositoryId=deploymentRepo 
          -Durl=http://192.168.33.10:8081/repository/maven-snapshots/ 
          -Dfile=target/ExamenThourayaS2-0.0.1-SNAPSHOT.jar 
          -Dnexus.login=admin -Dnexus.password=nexus "
  
   
        }
        }
        }
}
