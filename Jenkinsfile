pipeline { 

    environment { 

        registry = "ayushi04/jenkins" 

        registryCredential = 'dockerhub_id' 

        dockerImage = '' 

    }

    agent any 

    stages { 

        stage('Checkout') { 

            steps { 

                git 'https://github.com/AyushiChaudhary/Jenkins-Assign.git' 

            }

        } 

        stage('Docker build') { 

            steps { 

                script { 

                    dockerImage = docker.build registry + ":$BUILD_NUMBER" 

                }

            } 

        }

stage ('Approval'){
  input{
    message "Do you want to push docker image to docke hub?"
  }
    steps {
                sh 'echo "Pushing Image"'

              }
        }

        stage('Docker push') { 

            steps { 

                script { 

                    docker.withRegistry( '', registryCredential ) { 

                        dockerImage.push() 

                    }

                } 

            }

        } 


        

    }

}



