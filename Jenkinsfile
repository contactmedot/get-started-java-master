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
        stage('Create Docker Image Registry') {
            steps{
             
              script{
                  
                    // docker.withRegistry("https://myacrtemp.azurecr.io", 'acr_id') {
                    //     def testImage = docker.build("javaimagewithoutwebsphere:${env.BUILD_ID}", './')
                    //     testImage.push()
                        docker.withRegistry("https://registry.hub.docker.com",'docker_id') {
                        def testImage = docker.build("dockershivam2020/myjavaapp:${env.BUILD_ID}", './')
                        testImage.push()
                    }
                }
            }
         }
         stage('Deploy- using Helm') {  
            steps{         
            powershell('helm package ./javaapp')
             powershell('helm install javaappv4 javaapp-0.1.0.tgz')       
                          
            }
         }
    }
    
}