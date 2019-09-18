
node {

   stage('Clone Repository') {
        // Get some code from a GitHub repository
        git 'https://github.com/enenim2000/spring-petclinic.git'
    
   }
   stage('Build Maven Image') {
        docker.build("maven-build")
   }
   
   stage('Run Maven Container') {
       
        //Remove maven-build-container if it exisits
        bat " docker rm -f maven-build-container"
        
        //Run maven image
        bat "docker run --rm --name maven-build-container maven-build"
   }
   
   stage('Deploy Spring Boot Application') {
        
         //Remove maven-build-container if it exisits
        bat " docker rm -f java-deploy-container"
       
        bat "docker run --name java-deploy-container --volumes-from maven-build-container -d -p 8090:8080 denisdbell/petclinic-deploy"
   }

}
