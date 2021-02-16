pipeline {
    agent any
    tools {
        maven "Maven"
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
                             sh 'mvn clean package'
                            echo '************************************************************************'        
                            echo '************************************************************************'     
                            echo 'Building..'
            }
        }
    }
}