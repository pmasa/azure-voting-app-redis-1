pipeline {
  environment {
    registry = "pedromasa/azure-voting-front"
    registryCredential = 'dockerhub'
    dockerImage = ''
    GIT_REPO_NAME = "voting-app-redis-demo"
    GIT_USER_NAME = "pmasa"
    GIT_USER_EMAIL = "devopsmas@gmail.com"
    GIT_TOKEN = credentials('GithubToken')
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/pmasa/azure-voting-app-redis-1.git'
      }
    }
    stage('Building Docker image ') {
      steps{
        script {
          sh '''
          cd azure-vote
          docker build -t $registry:$BUILD_NUMBER .
          '''
          echo "Image build complete"
          //dockerImage = docker.build ./azure-vote registry + ":$BUILD_NUMBER"

          
        }
      }
    }

    stage('Push Image to Docker Hub') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            //dockerImage.push()
            //dockerImage.push('latest')
             sh "docker push $registry:$BUILD_NUMBER"
             echo "Image push complete"
          }
        }
      }
    }

    stage('Update Manifest'){
      steps{
        script{
            sh '''
                rm -rf ${GIT_REPO_NAME}
                git clone https://github.com/${GIT_USER_NAME}/${GIT_REPO_NAME}
                cd ${GIT_REPO_NAME}
                
                git config user.email ${GIT_USER_EMAIL}
                git config user.name devops
    
               cat deployment.yaml
               
               sed -i "s+$registry.*+$registry:${BUILD_NUMBER}+g" deployment.yaml 

               cat deployment.yaml
               
               git add .
               git commit -m "commit manifest file"
               git push https://${GIT_TOKEN}@github.com/${GIT_USER_NAME}/${GIT_REPO_NAME}.git HEAD:main -f
          '''
      }
    }
    }
  
  }
}  
