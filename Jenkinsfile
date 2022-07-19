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
                sh 'curl -fsSLO https://get.docker.com/builds/Linux/x86_64/docker-17.03.1-ce.tgz &&
                    tar --strip-components=1 -xvzf docker-17.03.1-ce.tgz -C /usr/local/bin'
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
