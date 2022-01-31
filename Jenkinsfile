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
         sh "npm install"
         sh "echo creating build artifacts ........... "
         sh 'tar czf Node.tar.gz node_modules index.js package.json'
      }
    }  
    
            
    stage('Deploy') {
      environment {
       // key = credentials("sshkey")
        cred = credentials("private_key")
      }
      steps {
        sh "echo Installling remote directory --------------------------"
        sh ('ssh -o \'StrictHostKeyChecking no\' -i \'$cred_PSW\'  $cred_USR@52.91.17.118 < setup_nvm_app_directory.txt')
        sh "echo Copying artifact to remote host directory ----------------------" 
        sh ('scp -i  $cred_PSW Node.tar.gz  $cred_USR@52.91.17.118:/home/ubuntu/node-app/')
        sh "echo Starting Node app on remote host ---------------------------------" 
        sh ('ssh -i $cred_PSW  $cred_USR@52.91.17.118 < startNode.txt')
        
      }
    }
  }
}
