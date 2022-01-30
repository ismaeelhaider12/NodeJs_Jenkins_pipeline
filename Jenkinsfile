pipeline {
  agent any
  environment {
    ssh_k = credentials("sshkey")
  }
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
        sh "echo succsessszssfully created"
        sh "whoami"
        sh "ls -la"
        sh " echo 'Some Text' | ssh -i ssh_k -o 'StrictHostKeyChecking no' ubuntu@3.84.55.80 -T 'cat > /home/ubuntu/ismaeeltesting.txt' "
      }
    }
  }
}
