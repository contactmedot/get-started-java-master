pipeline {
    agent any
    tools {
        maven "Maven-3.6.3"
    }
    environment {
                    HELM_EXPERIMENTAL_OCI=1
                    KUBECONFIG = 'C:/Users/shivam/.kube/config'
                }
    stages {
        stage('Build') { 
            steps {
                
                            echo '************************************************************************'        
                            echo '************************************************************************'     
                            echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                            echo "${env.JENKINS_HOME}"
                            echo "${env.WORKSPACE}"
                             bat 'mvn clean install'
                            echo '************************************************************************'        
                            echo '************************************************************************'     
                            echo 'Building..'
            }
        }
    }
}