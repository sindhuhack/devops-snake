node ('ubuntu-app-agent'){  
    def app
    stage('Cloning Git') {
        /* Let's make sure we have the repository cloned to our workspace */
       checkout scm
    }  
   
    
    stage('Build-and-Tag') {
       // sh 'echo Build-and-Tag'
    /* This builds the actual image; synonymous to
         * docker build on the command line */
       app = docker.build("sindhuhack/snake")
    }
    stage('Post-to-dockerhub') {
        sh 'echo Post-to-dockerhub'
    
     docker.withRegistry('https://registry.hub.docker.com', 'docker_cred') {
            app.push("latest")
        			} 
         }
  
    stage('Pull-image-server') {
        sh 'echo Pull-image-server'
    
         sh "docker-compose down"
         sh "docker-compose up -d" 	
      } 
}
