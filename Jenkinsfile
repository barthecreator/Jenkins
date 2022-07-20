pipeline {
 
 agent {label 'kubepod'}
 

  stages {
    stage('Git Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/barthecreator/Jenkins.git'
          
      }
    }
    

    stage('Test Jenkins Image'){
        steps{
            script{
                sh 'hostname'
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
  
