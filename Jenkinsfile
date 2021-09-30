currentBuild.displayName = "Final_Demo # "+currentBuild.number

   def getDockerTag(){
        def tag = sh script: 'git rev-parse HEAD', returnStdout: true
        return tag
        }
        

pipeline{
        agent any  
        environment{
	    Docker_tag = getDockerTag()
        }
        
        stages{
          stage('Build'){
                  steps{
                      script{
		    sh "mvn clean install"
                  }
                }  
              }
              stage('build')
                {
              steps{
                  script{
		 
                   sh 'docker build . -t deekshithsn/devops-training:$Docker_tag'
		   withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhub')]) {
				    
				  sh 'docker login -u raaghavendra -p $dockerhub'
				  sh 'docker push raaghavendra/devops-training:$Docker_tag'
			}
                       }
                    }
                 }
               }
	       
	       
	       
	      
    
}
