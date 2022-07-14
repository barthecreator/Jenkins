pipeline {
 
  agent { label 'kubepod'}
 
  
  stages {
    stage('Git Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/barthecreator/Jenkins.git'
          
      }
    }
    
    stage('Deploy To K8's){
      steps {
        KubernetesDeploy(configs: "deployment.yaml" , kubeconfigId: "kubernetes")
      }
    }
        
    
  }
 
}
