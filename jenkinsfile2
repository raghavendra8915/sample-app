def workspace
node {
    workspace = env.WORKSPACE
}
pipeline {
    agent any;
    parameters {
        string(name: 'JENKINS_WORKSPACE', defaultValue: workspace, description: 'Jenkins WORKSPACE')
    }
    stages {
        stage('access env variable') {
            steps {
                // in groovy
                echo "${env.WORKSPACE}"
                
                //in shell
                sh 'echo $WORKSPACE'
                
                // in groovy script 
                script {
                    print env.WORKSPACE
                }
            }
        }
    }
}
