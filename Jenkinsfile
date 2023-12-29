pipeline {
    agent any
    environment{
        ssh_key = credentials('ssh_key')
    }
    stages {

    
        stage('ssh connection'){
            steps{
                script{
                def sshCommand = """ssh -i ${ssh_key} ubuntu@ec2-13-200-255-210.ap-south-1.compute.amazonaws.com"""
                sh '$sshCommand'   
                }
            }
        }
        
        stage('checkout') {
             steps {
               git branch: 'uat', credentialsId: 'c95654d9-bda3-4cdc-a75d-6951e4211bfd', url: 'https://github.com/yadasManisha/jenkins.git'
                }
        }
        stage('deploy') {
            steps {
                sh '''                    
                    sudo apt update -y
                    sudo apt-get install python3 -y
                    cd /home/jenkins/workspace/flaskapp
                    pip3 install flask
                    nohup python3 app.py
                    ''' }
        }
        
    }
    
}
