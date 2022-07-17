pipeline {
 
 agent {label 'kubepod'}
 
  
  stages {
    stage('Git Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/barthecreator/Jenkins.git'
          
      }
    }
    
    stage('Deploy To Kubernetes'){
      steps {
       script {
         kubernetesDeploy(configs: "deployment.yaml", kubeconfigId: "kubernetes")
      }
    }
        
    
  }
 
}
