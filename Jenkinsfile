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
	    stage('count lines of code'){
              steps{
                  script{
		 
 //                  sh ' cloc  --csv --report-file=test.csv /var/lib/jenkins/workspace/test'
//	             sh 'cloc https://github.com/raghavendra8915/sample-app.git'
	             sh 'cloc  --csv --report-file=test.csv "$sample-app"'
			             }
                       }
                    }
          stage('Build'){
                  steps{
                      script{
		    sh "mvn clean install"
                  }
                }  
              }
              stage('docker image'){
              steps{
                  script{
		 
                   sh 'docker build . -t raaghavendra/testing:$Docker_tag'
		   withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhub')]) {
				    
				  sh 'docker login -u raaghavendra -p $dockerhub'
				  sh 'docker push raaghavendra/testing:$Docker_tag'
			            }
                       }
                    }
                 }
                 }
               } 
