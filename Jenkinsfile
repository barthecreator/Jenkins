pipeline {
 
 agent {
  kubernetes {
  yamlFile 'builder.yaml'
  }
 }
 

  stages {
    stage('Git Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/barthecreator/Jenkins.git'
          
      }
    }
    

    stage('Build image with Kaniko'){
        steps{
            container('kaniko'){
            script {
                sh 'hostname'
            }
        }
    }
    }
    
    stage('Deploy App to Kubernetes') {     
      steps {
        container('kubectl') {
          withCredentials([file(credentialsId: 'kubernetes', variable: 'KUBECONFIG')]) {
            sh 'sed -i "s/<TAG>/${BUILD_NUMBER}/" deployment.yaml'
            sh 'kubectl apply -f deployment.yaml'
          }
        }
      }
    }
        
    
  }
}
