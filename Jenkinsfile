pipeline {
 
 agent {label 'kubepod'}
 

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
                sh '''
                /kaniko/executor --dockerfile /Dockerfile \
                                 --context  \
                                 --destination=bargab/jenkisnbuildtest:${BUILD_NUMBER}
            '''
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
