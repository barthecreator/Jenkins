pipeline {
 
 agent {
  kubernetes {
  yamlFile 'builder.yaml'
  }
 }
 

  stages {
    stage('Git Clone') {
      steps {
        sh 'cat /etc/resolv.conf'
        sh 'git --version'
        git branch: 'main', url: 'https://github.com/barthecreator/Jenkins.git'
        
          
      }
    }
    

    stage('Build image with Kaniko'){
        steps{
            container('kaniko'){
            script {
                sh '''
                /kaniko/executor --dockerfile /Dockerfile \
                                 --context  \
                                 --destination=bargab/jenkisnbuildtest:${BUILD_NUMBER}
            '''
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
