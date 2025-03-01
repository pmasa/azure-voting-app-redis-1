pipeline {
  environment {
    registry = "pedromasa/azure-vote-front"
    registryCredential = 'dockerhub'
    dockerImage = ''
    GIT_REPO_NAME = "jenkins-gitops-k8s"
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
            dockerImage.push()
            //dockerImage.push('latest')
          }
        }
      }
    }

    //stage('Update Manifest'){
    //  steps{
    //    script{
    //        sh '''
    //            rm -rf ${GIT_REPO_NAME}
    //            git clone https://github.com/${GIT_USER_NAME}/${GIT_REPO_NAME}
    //            cd ${GIT_REPO_NAME}
    //            
    //            git config user.email ${GIT_USER_EMAIL}
    //            git config user.name devops
    //
    //           cat deployment.yaml
    //           sed -i "s+pedromasa/webapp.*+pedromasa/webapp:${BUILD_NUMBER}+g" deployment.yaml
    //           cat deployment.yaml
    //           
    //           git add .
    //           git commit -m "push manifest file"
    //           git push https://${GIT_TOKEN}@github.com/${GIT_USER_NAME}/${GIT_REPO_NAME}.git HEAD:main -f
    //      '''
    //  }
    //}
    //}
  
  }
}  
