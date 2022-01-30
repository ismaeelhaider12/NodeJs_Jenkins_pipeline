pipeline {
  agent any
  tools {nodejs "nodejs"}  
  stages {
        
    stage('Git') {
      steps {
        git branch: 'main', url: 'https://github.com/ismaeelhaider72/NodeJs_Jenkins_pipeline.git'
      }
    }
     
    stage('Build') {
      steps {
        sh 'npm install'
         sh 'tar czf Node.tar.gz node_modules index.js package.json'
      }
    }  
    
            
    stage('Deploy') {
      steps {
        sh "echo succsessszfully created"
        sh "whoami"
//         sh (script:"cat /home/ubuntu/key.pem")
        sh "ssh -i '/home/ubuntu/key.pem' ubuntu@3.84.55.80"
      }
    }
  }
}
