pipeline {
 
 agent {label 'kubepod'}
 
environment {
  dockerimagename = "bargab/jenkisnbuildtest"
  dockerImage = ""
  }
  stages {
    stage('Git Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/barthecreator/Jenkins.git'
          
      }
    }
    

    stage('Build image'){
        steps{
            script {
                dockerImage = docker.build dockerimagename
            }
        }
    }
    
    stage('Push Image'){
        environment {
            registryCredential = 'dockerhub'
           }
        steps{
            script{
            docker.withRegistry('https://registry.hub.docker.com', registryCredential ){
                dockerImage.push("latest")
            }
        }
        }
    
    }

    // stage('Deploy To Kubernetes'){
    //   steps {
    //    script {
    //      kubernetesDeploy(configs: "deployment.yaml", kubeconfigId: "kubernetes" , enableConfigSubstitution: false)
    //   }
    // }
        
    
  }
  } 
